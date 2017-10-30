---
title: "MySQL のデータ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d7c5a38-18d3-4cc9-a241-04422cb250d3
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3df56fcda5b39c2895de83feac4f302686b1adf3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-mysql-data-source-sql-server-import-and-export-wizard"></a>MySQL のデータ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **MySQL**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。 MySQL への接続に使用できるいくつかのデータ プロバイダーがあります。

> [!IMPORTANT]
> MySQL データベースに接続するための前提条件と要件の詳細については、この Microsoft の記事の範囲を超えています。 この記事では、MySQL クライアント ソフトウェアをインストール済みであることと、接続できることを既に正常にターゲットの MySQL データベースを前提としています。 詳細については、MySQL データベース管理者または MySQL のドキュメントを参照してください。

## <a name="get-the-mysql-connectors"></a>MySQL へのコネクタを取得します。
プロバイダーおよびからは、このトピックで説明されているドライバーをダウンロード、 [MySQL コネクタ](https://dev.mysql.com/downloads/connector/)ページ。

## <a name="connect-to-mysql-with-the-net-framework-data-provider-for-mysql"></a>.Net Framework Data Provider for MySQL MySQL を接続します。
選択した後**.NET Framework Data Provider for MySQL**で、**データ ソースを選択**または**変換先を選択**ページ、ウィザードのページには、プロバイダーのオプションのグループ化された一覧が表示されます。 これらの多くは、悪意のある名前と不明な設定です。 さいわい、のみ、いくつかの情報を提供する必要があります。 その他の設定の既定値は無視できます。

> [!NOTE]
> このデータ プロバイダーの接続オプションは、MySQL が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

|必要な情報|.Net framework Data Provider for MySQL プロパティ|
|---|---|
|サーバー名|**[サーバー]**|
|データベース名|**データベース**|
|認証 (ログイン) の情報|**ユーザー Id**と**パスワード**|

内の接続文字列を入力する必要はありません、 **ConnectionString**リストのフィールドです。 MySQL サーバー名の個々 の値を入力した後 (**サーバー**) し、ログイン情報、ウィザードでは、個々 のプロパティとその値から、接続文字列をアセンブルします。 

![プロバイダーでは、.NET、1/2 MySQL を接続します。](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-1-of-2.png)

![プロバイダーでは、.NET、2 の 2 MySQL を接続します。](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-2-of-2.png)

## <a name="connect-to-mysql-with-the-mysql-odbc-driver"></a>MySQL の ODBC ドライバーで MySQL への接続します。
ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 ODBC ドライバーで接続するを選択して開始、 **.NET Framework Data Provider for ODBC**上のデータ ソースとして、**データ ソースを選択**または**先選択**ページ。 このプロバイダーは、ODBC ドライバーをラップするラッパーとして機能します。

ここで、odbc、.NET Framework Data Provider を選択した後すぐに表示されているジェネリック画面です。

![前に odbc SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-mysql-odbc-driver"></a>(MySQL の ODBC ドライバー) を指定するオプション

> [!NOTE]
> このデータ プロバイダーと ODBC ドライバーの接続オプションは、MySQL が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

MySQL の ODBC ドライバーでは、MySQL に接続するには、次の設定とその値を含む接続文字列を編成します。 完全な接続文字列の書式設定の一覧の直後にします。

> [!TIP]
> 適切である接続文字列をアセンブル ヘルプを取得します。 接続文字列を提供するには、代わりに既存の DSN (データ ソース名) を提供または、新しいものを作成します。 これらのオプションの詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

**ドライバー**  
ODBC ドライバーの名前。

**[サーバー]**  
MySQL サーバーの名前。 

**データベース**  
MySQL データベースの名前。

**UID**と**PWD**   
ユーザー id とパスワードを接続します。

### <a name="connection-string-format"></a>接続文字列の形式
一般的な接続文字列の形式を次に示します。

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=<server>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>接続文字列を入力します。
内の接続文字列を入力、 **ConnectionString**フィールド、または DSN 名を入力、 **Dsn**フィールドに、**データ ソースを選択**または**変換先を選択**ページ。 接続文字列を入力すると後、ウィザードは、文字列を解析し、個々 のプロパティとその値を一覧に表示します。

次の例では、この接続文字列を使用します。

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=127.0.0.1;Database=world;UID=root;PWD=********
    ```

ここで、接続文字列を入力した後に表示される画面です。

![ODBC の MySQL への接続します。](../../integration-services/import-export-data/media/connect-to-mysql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>他のデータ プロバイダーと詳細情報
詳細については、ここに記載されていないデータ プロバイダーと MySQL を接続する方法は、次を参照してください。 [MySQL 接続文字列](https://www.connectionstrings.com/mysql/)です。 このサード パーティのサイトには、データ プロバイダーとこのページで説明されている接続パラメーターに関する詳細情報も含まれます。

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


