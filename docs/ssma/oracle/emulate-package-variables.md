---
title: Oracle パッケージ変数のエミュレーション
description: SQL Server Migration Assistant (SSMA) for Oracle が SQL Server で Oracle パッケージ変数をエミュレートする方法について説明します。
author: nahk-ivanov
ms.prod: sql
ms.technology: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: ab7de81e16d1324aabd5f07421c1db4c51b3cf7c
ms.sourcegitcommit: e572f1642f588b8c4c75bc9ea6adf4ccd48a353b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84779464"
---
# <a name="emulating-oracle-package-variables"></a>Oracle パッケージ変数のエミュレーション

Oracle では、変数、型、ストアドプロシージャ、および関数をパッケージにカプセル化できます。 Oracle パッケージを変換する場合は、次の変換を行う必要があります。

* プロシージャと関数-パブリックとプライベートの両方
* 変数
* カーソル
* 初期化ルーチン

この記事では、SQL Server Migration Assistant (SSMA) for Oracle でパッケージ変数を SQL Server に変換する方法について説明します。

## <a name="conversion-basics"></a>変換の基礎

SSMA for Oracle では、パッケージ変数を格納するために、テーブルと共に特別なスキーマに存在するストアドプロシージャを使用し `ssma_oracle` `ssma_oracle.db_storage` ます。 このテーブルは `SPID` 、(セッション識別子) とログイン時間によってフィルター処理されます。 このフィルターを使用すると、異なるセッションの変数を区別できます。

変換された各パッケージの先頭で、SSMA は特殊なプロシージャへの呼び出しを `ssma_oracle.db_check_init_package` 行います。このプロシージャは、パッケージが初期化されているかどうかを確認し、必要に応じて初期化します。 各初期化プロシージャは、ストレージテーブルをクリーンアップし、各パッケージ変数の既定値を設定します。

## <a name="example"></a>例

いくつかのパッケージ変数を変換する場合は、次の例を考えてみます。

```sql
CREATE OR REPLACE PACKAGE MY_PACKAGE
IS
    space varchar(1) := ' ';
    unitname varchar(128) := 'My Simple Package';
    ts date := sysdate;
END;
```

SSMA は、次の Transact-sql コードに変換します。

```sql
CREATE PROCEDURE dbo.MY_PACKAGE$SSMA_Initialize_Package
AS
BEGIN
    EXECUTE ssma_oracle.db_clean_storage

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'SPACE',
        ' '

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'UNITNAME',
        'My Simple Package'

    DECLARE
        @temp datetime2

    SET @temp = sysdatetime()

    EXECUTE sysdb.ssma_oracle.set_pv_datetime2
      DB_NAME(),
      'DBO',
      'MY_PACKAGE',
      'TS',
      @temp
END
```

## <a name="emulating-get-and-set-methods-for-package-variables"></a>パッケージ変数の Get メソッドと Set メソッドのエミュレーション

Oracle では、 `Get` `Set` パッケージ変数にメソッドとメソッドを使用して、他のサブプログラムが直接読み取りおよび書き込みを行わないようにします。 同じセッション内の subprogram 呼び出し間で使用できる変数を保持する必要がある場合、これらの変数はグローバル変数と同様に扱われます。

SSMA for Oracle では、このスコープルールを克服するために、 `ssma_oracle.set_pv_varchar` 変数の型ごとにのようなストアドプロシージャを使用します。 これらの変数にアクセスするために、SSMA は、一連のトランザクションに依存 `get_*` しない `set_*` プロシージャと関数を使用します。

| Oracle でのデータ型 | SSMA `Set` プロシージャ           |
| ------------------- | ------------------------------ |
| VARCHAR             | `ssma_oracle.set_pv_varchar`   |
| DATE                | `ssma_oracle.set_pv_datetime2` |
| CHAR                | `ssma_oracle.set_pv_varchar`   |
| INT                 | `ssma_oracle.set_pv_float`     |
| FLOAT               | `ssma_oracle.set_pv_float`     |

SSMA では、異なるセッションの変数を区別するために、 `SPID` (セッション識別子) とセッションのログイン時間と共に変数を格納します。 したがって、 `get_*` プロシージャとプロシージャを実行すると、 `set_*` 変数は、それらを実行するセッションから独立して保持されます。
