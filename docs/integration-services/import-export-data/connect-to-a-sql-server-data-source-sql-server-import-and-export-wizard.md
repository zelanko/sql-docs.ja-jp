---
title: "SQL Server のデータ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
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
ms.assetid: 386cedbb-fae5-45ce-9363-c4a417f80a2f
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 17910c8e30dee98f39e977896fb67774b54a798d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard"></a>SQL Server のデータ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **Microsoft SQL Server**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。 SQL Server への接続に使用できるいくつかのデータ プロバイダーがあります。

> [!TIP]
> 複数のサーバーを使用したネットワーク上にする場合は、サーバーのドロップダウン リストを展開するのではなく、サーバー名を入力しやすい場合があります。 ドロップダウン リストをクリックすると、多くのすべての利用可能なサーバーのネットワークを照会する時間がかかる場合があり、結果はも含まれていないか、サーバーです。

## <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>.NET Framework Data Provider for SQL Server を使用して SQL Server に接続する 
選択した後**.NET Framework Data Provider for SQL Server**上、**データ ソースを選択**または**変換先を選択**ページ、ウィザードのページには、プロバイダーのオプションのグループ化された一覧が表示されます。 これらの多くは、悪意のある名前と不明な設定です。 幸いにも、エンタープライズ データベースに接続するに通常指定する必要が情報のいくつかの部分のみです。 その他の設定の既定値は無視できます。

> [!NOTE]
> このデータ プロバイダーの接続オプションは、SQL Server が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

|必要な情報|.Net framework Data Provider for SQL Server プロパティ|
|---|---|
|サーバー名|**[データ ソース]**|
|認証 (ログイン) の情報|**統合セキュリティ**; または、**ユーザー ID**と**パスワード**<br/>サーバー上のデータベースのボックスの一覧を表示する場合は、まず、有効なログイン情報を提供する必要があります。|
|データベース名|**初期カタログ**|

![.NET プロバイダーで SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-net-provider.jpg)

### <a name="options-to-specify-net-framework-data-provider-for-sql-server"></a>(.NET Framework Data Provider for SQL Server) を指定するオプション

> [!NOTE]
> このデータ プロバイダーの接続オプションは、SQL Server が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

**[データ ソース]**  
 名前または送信元または送信先のサーバーの IP アドレスを入力するか、ドロップダウン リストからサーバーを選択します。  
 
 非標準の TCP ポートを指定するには、サーバー名または IP アドレスの後にコンマを入力し、ポート番号を入力します。
 
 **初期カタログ**  
 元または転送先のデータベースの名前を入力するか、ドロップダウン リストからデータベースを選択します。  
  
 **統合セキュリティ**  
 指定**True** (推奨)、Windows 統合認証で接続するまたは**False**に接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **False** を指定した場合は、ユーザー ID とパスワードを入力する必要があります。 既定値は **False**です。  
  
 **[ユーザー ID]**  
 使用する場合は、ユーザー名を入力[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  
  
 **Password**  
 使用している場合、パスワードの入力[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  

## <a name="connect-to-sql-server-with-the-odbc-driver-for-sql-server"></a>SQL Server 用 ODBC ドライバーで SQL Server に接続します。 
ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 ODBC ドライバーで接続するを選択して開始、 **.NET Framework Data Provider for ODBC**データ ソースとして。 このプロバイダーは、ODBC ドライバーをラップするラッパーとして機能します。

> [!TIP]
> **最新のドライバーを入手**です。 ダウンロード、 [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)です。

ここで、odbc、.NET Framework Data Provider を選択した後すぐに表示されているジェネリック画面です。

![前に odbc SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-sql-server"></a>(SQL Server 用 ODBC driver) を指定するオプション

> [!NOTE]
> ODBC ドライバーの接続オプションは、SQL Server が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

最新の ODBC ドライバーで SQL Server に接続するには、次の設定とその値を含む接続文字列を編成します。 完全な接続文字列の書式設定の一覧の直後にします。

> [!TIP]
> 適切である接続文字列をアセンブル ヘルプを取得します。 接続文字列を提供するには、代わりに既存の DSN (データ ソース名) を提供または、新しいものを作成します。 これらのオプションの詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

**ドライバー**  
ODBC ドライバーの名前。 名前は、ドライバーのバージョンによって異なる。

**[サーバー]**  
SQL Server の名前。

**データベース**  
データベースの名前。  

**Trusted_Connection**; または、 **Uid**と**Pwd**  
指定**Trusted_Connection = [はい]** Windows 統合認証で接続するか、指定する**Uid** (ユーザー id) と**Pwd** SQL Server 認証で接続するには、(パスワード)。

### <a name="connection-string-format"></a>接続文字列の形式
Windows 統合認証を使用する接続文字列の形式を次に示します。

    `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;trusted_connection=Yes;`

Windows 統合認証ではなく SQL Server 認証を使用する接続文字列の形式を次に示します。

     `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;uid=<user id>;pwd=<password>;`

### <a name="enter-the-connection-string"></a>接続文字列を入力します。
内の接続文字列を入力、 **ConnectionString**フィールド、または DSN 名を入力、 **Dsn**フィールドに、**データ ソースを選択**または**変換先を選択**ページ。 接続文字列を入力すると後、ウィザードは、文字列を解析し、個々 のプロパティとその値を一覧に表示します。

次の例では、この接続文字列を使用します。

    `Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;`

ここで、接続文字列を入力した後に表示される画面です。

![後の odbc SQL への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="connect-to-sql-server-with-the-microsoft-ole-db-provider-for-sql-server-or-sql-server-native-client"></a>SQL Server または SQL Server Native Client の Microsoft OLE DB プロバイダーでの SQL Server に接続します。

> [!IMPORTANT]
> Microsoft OLE DB Provider for SQL Server と SQL Server Native Client は、SQL Server 2012 以降後のバージョンの SQL Server でサポートされていません。 代わりに、ODBC ドライバーを使用します。 ODBC ドライバーへの移行に関する詳細については、次のブログの投稿を参照してください。
>   -   [Microsoft はネイティブのリレーショナル データ アクセス用の odbc 整列します。](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)
>   -   [新しい Microsoft ODBC Drivers for SQL Server の概要](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/)

## <a name="other-data-providers-and-more-info"></a>他のデータ プロバイダーと詳細情報
詳細については、ここに記載されていないデータ プロバイダーと SQL Server に接続する方法は、次を参照してください。 [SQL Server 接続文字列](https://www.connectionstrings.com/sql-server/)です。 このサード パーティのサイトには、データ プロバイダーとこのページで説明されている接続パラメーターに関する詳細情報も含まれます。

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


