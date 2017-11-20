---
title: "PostgreSQL データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7a75a72-b267-444f-9eb8-d23eb333fc35
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4c82ae7eedc3e18e7591cf7ab30a507920695247
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard"></a>PostgreSQL データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **PostgreSQL**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。 

> [!IMPORTANT]
> PostgreSQL データベースに接続するための前提条件と要件の詳細については、この Microsoft の記事の範囲を超えています。 この記事では、PostgreSQL クライアント ソフトウェアをインストール済みであることと、接続できることを既に正常にターゲット PostgreSQL データベースを前提としています。 詳細については、PostgreSQL データベース管理者または PostgreSQL のドキュメントを参照してください。

## <a name="get-the-postgresql-odbc-driver"></a>PostgreSQL ODBC ドライバーを入手します。

### <a name="install-the-odbc-driver-with-stack-builder"></a>スタック ビルダーでの ODBC ドライバーをインストールします。
PostgreSQL ODBC ドライバー (psqlODBC) PostgreSQL のインストールを追加するスタック ビルダーを実行します。

![スタック ビルダー PostgreSQL ODBC をインストールします。](../../integration-services/import-export-data/media/install-postgresql-odbc-with-stack-builder.png)

### <a name="or-download-the-latest-odbc-driver"></a>また、最新の ODBC ドライバーのダウンロード
-この FTP サイトから直接 PostgreSQL ODBC ドライバー (psqlODBC) の最新バージョンの Windows インストーラーのダウンロードや、 [https://www.postgresql.org/ftp/odbc/versions/msi/](https://www.postgresql.org/ftp/odbc/versions/msi/)です。 .Zip ファイルからファイルを抽出し、.msi ファイルを実行します。

## <a name="connect-to-postgresql-with-the-postgresql-odbc-driver-psqlodbc"></a>PostgreSQL PostgreSQL ODBC ドライバー (psqlODBC) に接続します。
ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 ODBC ドライバーで接続するを選択して開始、 **.NET Framework Data Provider for ODBC**上のデータ ソースとして、**データ ソースを選択**または**先選択**ページ。 このプロバイダーは、ODBC ドライバーをラップするラッパーとして機能します。

ここで、odbc、.NET Framework Data Provider を選択した後すぐに表示されているジェネリック画面です。

![前に odbc PostgreSQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-postgresql-odbc-driver"></a>(PostgreSQL ODBC ドライバー) を指定するオプション

> [!NOTE]
> PostgreSQL が、ソースまたは変換先であるかどうか、このデータ プロバイダーと ODBC ドライバーの接続オプションは、同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

PostgreSQL PostgreSQL ODBC ドライバーで接続するには、次の設定とその値を含む接続文字列を編成します。 完全な接続文字列の書式設定の一覧の直後にします。

> [!TIP]
> 適切である接続文字列をアセンブル ヘルプを取得します。 接続文字列を提供するには、代わりに既存の DSN (データ ソース名) を提供または、新しいものを作成します。 これらのオプションの詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

**ドライバー**  
ODBC ドライバーの - か、名前**PostgreSQL ODBC Driver(UNICODE)**または**PostgreSQL ODBC Driver(ANSI)**です。

**[サーバー]**  
PostgreSQL サーバーの名前。 

**ポート**  
PostgreSQL サーバーへの接続に使用するポート。

**データベース**  
PostgreSQL データベースの名前。

**Uid**と**Pwd**   
**Uid** (ユーザー id) と**Pwd** (パスワード) に接続します。

### <a name="connection-string-format"></a>接続文字列の形式
一般的な接続文字列の形式を次に示します。 

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=<server>;Port=<port>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>接続文字列を入力します。
内の接続文字列を入力、 **ConnectionString**フィールド、または DSN 名を入力、 **Dsn**フィールドに、**データ ソースを選択**または**変換先を選択**ページ。 接続文字列を入力すると後、ウィザードは、文字列を解析し、個々 のプロパティとその値を一覧に表示します。

次の例では、この接続文字列を使用します。

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=127.0.0.1;Port=5432;Database=postgres;UID=postgres;PWD=********
    ```

ここで、接続文字列を入力した後に表示される画面です。

![Odbc PostgreSQL への接続します。](../../integration-services/import-export-data/media/connect-to-postgresql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>他のデータ プロバイダーと詳細情報
詳細については、ここに記載されていないデータ プロバイダーと PostgreSQL に接続する方法は、次を参照してください。 [PostgreSQL 接続文字列](https://www.connectionstrings.com/postgresql/)です。 このサード パーティのサイトには、データ プロバイダーとこのページで説明されている接続パラメーターに関する詳細情報も含まれます。

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


