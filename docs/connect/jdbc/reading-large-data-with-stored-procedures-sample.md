---
title: ストアド プロシージャで大きなデータを読み取るサンプル | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8277cafb173dc28876c95a7ccb60f7ed3ee6396a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66772478"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>ストアド プロシージャで大きなデータを読み取るサンプル

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、ストアド プロシージャから大きな OUT パラメーターを取得する方法を示しています。

このサンプルのコード ファイルは ExecuteStoredProcedure.java という名前で、次の場所にあります。

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>必要条件

このサンプル アプリケーションを実行するには、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースへのアクセス権が必要です。 また、クラスパスの設定で mssql-jdbc jar ファイルを追加する必要があります。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)します。

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、必要な Java ランタイム環境 (JRE) 設定に応じて使用される mssql-jdbc クラス ライブラリ ファイルが用意されています。 選択する JAR ファイルの詳細については、「[JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)」を参照してください。

サンプルで必要なストアド プロシージャの作成は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。

## <a name="example"></a>例

次の例のサンプル コードでは、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] データベースへの接続を行います。 次に、サンプル データを作成し、パラメーター化クエリを使用して Production.Document テーブルを更新します。 さらに、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) メソッドを使用してアダプティブ バッファリング モードを取得し、GetLargeDataValue ストアド プロシージャを実行します。 JDBC Driver Version 2.0 リリース以降では、responseBuffering 接続プロパティが既定で "adaptive" に設定されています。

最後に、OUT パラメーターで返されたデータを表示します。また、ストリームに対して `mark` メソッドと `reset` メソッドを使用して、データの任意の部分を再度読み取る方法も示しています。

[!code[JDBC#UsingAdaptiveBuffering2](../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>参照

[大きなデータの処理](../../connect/jdbc/working-with-large-data.md)
