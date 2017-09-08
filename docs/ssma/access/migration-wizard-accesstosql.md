---
title: "移行ウィザード (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Migration Wizard dialog box
- Migration Wizard, adding Access databases
- Migration Wizard, Connect to SQL Azure
- Migration Wizard, Connect to SQL Server
- Migration Wizard, Link Tables
- Migration Wizard, Migration status
- Migration Wizard, New Project
- Migration Wizard, Selecting objects to migrate
ms.assetid: 5bab5914-b2ae-4795-8cf5-83e42d64bef2
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e6b2024b8ba34bd4f71abc6030ae86dcc03faebd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migration-wizard-accesstosql"></a>移行ウィザード (AccessToSQL)
移行ウィザードで、1 つまたは複数のデータベースの移行へのアクセスを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 ウィザードを使用するがプロジェクトを作成、データベースをプロジェクトに追加されたら、オブジェクトを移行し、接続を選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 また変換、読み込むには、し、アクセスのスキーマとデータを移行します。 Access テーブルをリンクする必要に応じて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルです。  
  
ほとんど移行ウィザード ページにはには、既存の SSMA ダイアログ ボックスと同じオプションが含まれます。 そのため、ウィザードのページが、ここで説明されているし、リンク情報も個別のオプションに関する詳細を提供します。 ページ固有のオプションが含まれている場合、次に示します。  
  
## <a name="starting-the-migration-wizard"></a>移行ウィザードの開始  
既定では、移行ウィザードは、SSMA を起動するときに表示されます。 ウィザードを開始することもできます、**ファイル**メニューを選択して**移行ウィザード**です。  
  
## <a name="welcome-page"></a>[ようこそ] ページ  
[ようこそ] ページでは、移行ウィザードを紹介し、ウィザードを開始するための次のオプションを提供します。  
  
**スタートアップ時に、このウィザードを起動します。**  
既定では、SSMA を起動するときに、SSMA は、移行ウィザードを開始します。 ウィザードの自動開始を防ぐためには、このチェック ボックスをオフにします。  
  
## <a name="create-new-project-page"></a>[新しいプロジェクト] ページを作成します。  
新しいプロジェクトの作成 ページは、プロジェクト ファイル名、場所、および移行プロジェクトの種類 (target の移行に使用する SQL Server のバージョン) を入力する場所です。 詳細については、次を参照してください[新しいプロジェクト (SSMA)。](http://msdn.microsoft.com/en-us/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>Access データベース ページを追加します。  
Access データベースの追加ページには、プロジェクトに 1 つまたは複数の Access データベースを追加します。 クリックして個々 のデータベースを追加することができます**データベースの追加**からデータベースを選択し、**開く**ウィンドウです。 または、使用してデータベースを検索することができます、**検索データベース**ボタンをクリックします。 詳細については、次の各トピックを参照してください。  
  
-   [追加して、Access データベース ファイルを削除します。](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)  
  
-   [データベースのウィザード (場所) を検索します。](http://msdn.microsoft.com/en-us/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [データベースのウィザード (ファイル) を検索します。](http://msdn.microsoft.com/en-us/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [データベースのウィザード (選択を確認する)](http://msdn.microsoft.com/en-us/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>オブジェクトの移行 ページを選択します。  
オブジェクトの移行 ページを選択では、変換するオブジェクトを選択します。 すべてのオブジェクト、オブジェクト、または個々 のオブジェクトのグループを選択することができます。  
  
**オブジェクトを選択するには**  
  
1.  展開**アクセス メタベース**の順に展開および**データベース**です。  
  
2.  次の 1 つ以上の操作を行います。  
  
    -   すべてのデータベースを変換するには、チェック ボックスを横に選択**データベース**です。  
  
    -   変換するか、個々 のデータベースを省略、オンまたはデータベース名の横にあるチェック ボックスをオフにします。  
  
    -   変換またはクエリの省略は、データベースを展開しをオンまたはオフ、**クエリ**チェック ボックスをオンします。  
  
    -   変換または個々 のテーブルの省略は、データベースを展開し、**テーブル**を選択するか、テーブルの横にあるチェック ボックスをオフにします。  
  
多くのオブジェクトがあればが使用する、**高度なオブジェクトの選択**データベース オブジェクトのアクセスをフィルター処理を右側のペインでオプションです。 例では、選択した場合の**テーブル**左側のウィンドウで、フィルター処理できますテーブルの一覧内の文字列を入力して、**フィルター**ボックス。 選択したり、ウィンドウの上部にあるボタンを使用して、フィルター選択されたテーブルの移行をオフにできます。  
  
フィルター処理の詳細については、の [オプション] セクションを参照してください。[高度なオブジェクトの選択 (SSMA 共通)](http://msdn.microsoft.com/en-us/f53b0c79-5473-410a-a0dc-d8f544f7a63c)です。  
  
## <a name="connect-to-sql-server-page"></a>SQL Server のページへの接続します。  
接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ページで、接続プロパティを指定しに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください[SQL Server への接続。](http://msdn.microsoft.com/en-us/00e0432e-ec26-4ab4-af64-c9ca760e3541)  
  
> [!IMPORTANT]  
> 発生すると、接続が成功すると、すぐに**リンク テーブル**ページ リンク、テーブルのオプションがあります。 をクリックして**次**し、移行を開始します。  
  
## <a name="connect-to-sql-azure-page"></a>SQL への接続 Azure のページ  
SQL Azure のページへの接続では、接続のプロパティを指定し、SQL Azure に接続し、します。 新しい azure データベースを作成するには、これを行うを使用して**Azure データベースの作成**のクリックで表示されるオプション**参照**ボタンをクリックします。 詳細については、次を参照してください[SQL Azure への接続。](http://msdn.microsoft.com/en-us/bf44b236-d9be-41ae-a5fd-bd73038e505f)  
  
> [!IMPORTANT]  
> 発生すると、接続が成功すると、すぐに**リンク テーブル**ページ リンク、テーブルのオプションがあります。 をクリックして**[次へ]**移行を開始するリンクのページにボタンをクリックします。  
  
## <a name="link-tables-page"></a>リンク テーブル ページ  
リンク テーブル ページでは、移行後に元の Access テーブルをリンクできます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルです。 Access データベースが変更テーブルをリンクするクエリ、フォーム、レポート、およびデータ アクセスのページ内のデータを使用するように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Access データベース内のデータではなく SQL Azure データベース。  
  
**テーブルなリンク**  
選択、**テーブルをリンク**移行後の Access テーブルをリンクする チェック ボックス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルです。 クリックする必要がありますの移行を開始する**次**ボタンをクリックします。  
  
## <a name="migration-status-page"></a>移行の状態 ページ  
移行の状態 ページにアクセス スキーマの変換の進行状況が表示[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のスキーマへの変換後のスキーマを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure では、データを移行するとします。  
  
このページの詳細については、次を参照してください[変換、読み込み、および移行。](http://msdn.microsoft.com/en-us/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>参照  
[For アクセス &#40; SQL Server Migration Assistant の概要AccessToSQL &#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[ユーザー インターフェイス Reference(Access)](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  

