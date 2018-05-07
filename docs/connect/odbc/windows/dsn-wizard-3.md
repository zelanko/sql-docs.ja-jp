---
title: データ ソース ウィザード画面 3 (SQL Server 用 ODBC Driver) |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbbedb76089ffb508f6ce521bd831b213ba90fc5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-wizard-screen-3"></a>データ ソース ウィザード画面 3

既定のデータベース、ドライバーで使用されるさまざまな ANSI オプション、およびミラー サーバーの名前を指定します。

## <a name="options"></a>オプション

### <a name="change-the-default-database-to"></a>既定のデータベースに変更します。

データ ソースを使用して確立された任意の接続に既定のデータベース名を指定します。 このチェック ボックスがオフの場合、接続は、サーバーのログイン ID に対して定義されている既定のデータベースを使用します。 このチェック ボックスがオンの場合、ボックスで指定されたデータベースが、ログイン ID に対して定義されている既定のデータベースよりも優先されます。 場合、**データベースのファイル名をアタッチ**ボックスには、プライマリ ファイルの名前、プライマリ ファイルに記述されたデータベースがで指定されたデータベース名を使用してデータベースとしてアタッチ、 **に既定のデータベースを変更**ボックス。

ログイン ID の既定のデータベースを使用するのは、ODBC データ ソースに既定のデータベースを指定するよりも効率的です。

### <a name="mirror-server"></a>ミラー サーバー

ミラー化するデータベースのフェールオーバー パートナーの名前を指定します。 データベース名が表示されていない場合、**に既定のデータベース変更**は既定のデータベースのボックスで、または表示名**ミラー サーバー**は淡色表示します。

必要に応じて、ミラー サーバーにサーバー プリンシパル名 (SPN) を指定できます。 ミラー サーバーの SPN は、クライアントとサーバー間の相互認証に使用されます。

### <a name="attach-database-filename"></a>データベースのファイル名をアタッチします。

アタッチできるデータベースのプライマリ ファイルの名前を指定します。 このデータベースがアタッチされ、データ ソースの既定のデータベースとして使用されます。 プライマリ ファイルの完全なパスとファイル名を指定します。 指定されたデータベース名、**に既定のデータベース変更**ボックスは、アタッチされたデータベースの名前として使用します。

### <a name="use-ansi-quoted-identifiers"></a>ANSI の引用符付き識別子を使用します。

SQL Server 用 ODBC ドライバーが接続するときに、QUOTED_IDENTIFIERS に設定することを指定します。 このチェック ボックスがオンの場合、SQL Server は、引用符に関する ANSI 規則を適用します。 二重引用符は、列名やテーブル名など、識別子のみに使用できます。 文字列は単一引用符で囲む必要があります。

```
SELECT "LastName"
FROM "Person.Contact"
WHERE "LastName" = 'O''Brien'
```

このチェック ボックスがオフの場合、Microsoft Excel に付属の Microsoft Query ユーティリティなど、引用符で囲まれた識別子を使用するアプリケーションでは、引用符で囲まれた識別子を使用した SQL ステートメントを生成するとエラーが発生します。

### <a name="use-ansi-nulls-paddings-and-warnings"></a>ANSI null、埋め込み文字、および警告を使用します。

ODBC Driver for SQL Server に接続するときに、ANSI_NULLS、ANSI_WARNINGS、および ANSI_PADDINGS のオプションに設定することを指定します。

ANSI_NULLS がオンに設定されている場合、サーバーでは、NULL に対する列の比較に関する ANSI 規則が適用されます。 ANSI 構文 "IS NULL" または "IS NOT NULL" は、すべての NULL 比較に使用する必要があります。 Transact-SQL 構文 "= NULL" はサポートされていません。

ANSI_WARNINGS の設定には、SQL Server は、ANSI 規則に違反が TRANSACT-SQL の規則に違反していない条件に対する警告メッセージを発行します。 このようなエラーの例として、INSERT ステートメントまたは UPDATE ステートメント実行時のデータの切り捨て、または集計関数での NULL 値の検出があります。 

ANSI_PADDING を on に設定を後続の空白にして**varchar** 、値を後ろにゼロに**varbinary**値は自動的に切り捨てられません。

### <a name="application-intent"></a>[アプリケーション インテント]

アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。

### <a name="multi-subnet-failover"></a>[マルチサブネット フェールオーバー]

アプリケーションが、高可用性、災害復旧 (AlwaysOn 可用性グループ) の可用性グループ (AG 異なるサブネット上) に接続している場合に有効にすると**マルチ サブネット フェールオーバー。** 迅速に検出し、(現在) アクティブなサーバーへの接続を提供する SQL Server 用 ODBC ドライバーを構成します。

### <a name="transparent-network-ip-resolution"></a>透過ネットワーク IP 解決します。

動作を変更**マルチ サブネット フェールオーバー**フェールオーバー中に短時間で再接続を許可します。 参照してください[透過的なネットワーク IP 解決を使用して](../../../connect/odbc/using-transparent-network-ip-resolution.md)詳細についてはします。

### <a name="column-encryption"></a>列の暗号化します。

により、自動暗号化解除およびとで暗号化された列からのデータ転送の暗号化、 [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) SQL Server 2016 では使用し、後で機能します。

### <a name="use-fmtonly-metadata-discovery"></a>FMTONLY メタデータの検出を使用します。

SQL Server 2012 への接続中またはそれ以降の場合は、従来の SET FMTONLY メタデータの検出方法を使用します。 サポートされていないクエリを使用する場合にのみ、このファイルを有効にする[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)、一時テーブルが含まれるものなどです。 

### <a name="next"></a>Next

ウィザードの次の画面に進みます。

### <a name="back"></a>戻る

ウィザードの前の画面に戻ります。

## <a name="next-steps"></a>次の手順

[データ ソース ウィザード画面 2](../../../connect/odbc/windows/dsn-wizard-2.md)

[データ ソース ウィザード画面 4](../../../connect/odbc/windows/dsn-wizard-4.md)
