---
title: "Oracle データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0bd1f5a-34dd-4be3-9ac8-f9f87727781b
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e589e7f7a0262d258342bf887ec84c57d57dc978
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-oracle-data-source-sql-server-import-and-export-wizard"></a>Oracle データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **Oracle**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。 Oracle への接続に使用できるいくつかのデータ プロバイダーがあります。

> [!IMPORTANT]
> Oracle データベースに接続するための前提条件と要件の詳細については、この Microsoft の記事の範囲を超えています。 この記事では、Oracle クライアント ソフトウェアをインストール済みであることと、接続できることを既に正常にターゲットの Oracle データベースを前提としています。 詳細については、Oracle データベース管理者または Oracle のマニュアルを参照してください。

## <a name="connect-to-oracle-with-the-net-framework-data-provider-for-oracle"></a>Oracle への接続で、.Net Framework Data Provider for Oracle
選択した後**.NET Framework Data Provider for Oracle**で、**データ ソースを選択**または**変換先を選択**ページ、ウィザードのページには、プロバイダーのオプションのグループ化された一覧が表示されます。 これらの多くは、悪意のある名前と不明な設定です。 幸いにも、2、3 つの情報を指定する必要がのみです。 その他の設定の既定値は無視できます。

> [!NOTE]
> このデータ プロバイダーの接続オプションは、Oracle が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

|必要な情報|.Net framework Data Provider for Oracle プロパティ|
|---|---|
|サーバー名|**[データ ソース]**|
|認証 (ログイン) の情報|**ユーザー ID**と**パスワード**; または、**統合セキュリティ**|

内の接続文字列を入力する必要はありません、 **ConnectionString**リストのフィールドです。 Oracle サーバー名の個々 の値を入力した後 (**データ ソース**) し、ログイン情報、ウィザードでは、個々 のプロパティとその値から、接続文字列をアセンブルします。 

![.NET プロバイダーで Oracle への接続します。](../../integration-services/import-export-data/media/connect-to-oracle-with-net-provider.jpg)

## <a name="connect-to-oracle-with-the-microsoft-odbc-driver-for-oracle"></a>Oracle 用 Microsoft ODBC ドライバーで Oracle への接続します。
ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 ODBC ドライバーで接続するを選択して開始、 **.NET Framework Data Provider for ODBC**上のデータ ソースとして、**データ ソースを選択**または**先選択**ページ。 このプロバイダーは、ODBC ドライバーをラップするラッパーとして機能します。

ここで、odbc、.NET Framework Data Provider を選択した後すぐに表示されているジェネリック画面です。

![前に odbc Oracle への接続します。](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-oracle"></a>(Oracle 用の ODBC ドライバー) を指定するオプション

> [!NOTE]
> このデータ プロバイダーと ODBC ドライバーの接続オプションは、Oracle が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

ODBC Driver for Oracle で Oracle に接続するには、次の設定とその値を含む接続文字列を編成します。 完全な接続文字列の書式設定の一覧の直後にします。

> [!TIP]
> 適切である接続文字列をアセンブル ヘルプを取得します。 接続文字列を提供するには、代わりに既存の DSN (データ ソース名) を提供または、新しいものを作成します。 これらのオプションの詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

**ドライバー**  
ODBC ドライバーの名前**Oracle 用 Microsoft ODBC**です。

**[サーバー]**  
Oracle サーバーの名前。 

**Uid**と**Pwd**   
ユーザー id とパスワードを接続します。

### <a name="connection-string-format"></a>接続文字列の形式
一般的な接続文字列の形式を次に示します。

    Driver={Microsoft ODBC for Oracle};Server=myServerAddress;Uid=myUsername;Pwd=myPassword;

### <a name="enter-the-connection-string"></a>接続文字列を入力します。
内の接続文字列を入力、 **ConnectionString**フィールド、または DSN 名を入力、 **Dsn**フィールドに、**データ ソースを選択**または**変換先を選択**ページ。 接続文字列を入力すると後、ウィザードは、文字列を解析し、個々 のプロパティとその値を一覧に表示します。

ここで、接続文字列を入力した後に表示される画面です。

![ODBC で Oracle への接続します。](../../integration-services/import-export-data/media/connect-to-oracle-with-odbc.jpg)

## <a name="whats-my-oracle-server-name"></a>Oracle サーバー名とは何ですか。
次のクエリを使用する Oracle サーバーの名前を取得する 1 つを実行します。

`SELECT host_name FROM v$instance`

または

`SELECT sys_context('USERENV','SERVER_HOST') FROM dual`

## <a name="other-data-providers-and-more-info"></a>他のデータ プロバイダーと詳細情報
詳細については、ここに記載されていないデータ プロバイダーと Oracle に接続する方法は、次を参照してください。 [Oracle 接続文字列](https://www.connectionstrings.com/oracle/)です。 このサード パーティのサイトには、データ プロバイダーとこのページで説明されている接続パラメーターに関する詳細情報も含まれます。

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


