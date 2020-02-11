---
title: '[データ ソースの選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b6e399cf6c145f36febd9b32ae7a84c54741bb43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62893597"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>[データ ソースの選択] (SQL Server インポートおよびエクスポート ウィザード)
  [**データソースの選択**] ページを使用すると、コピーするデータのソースを指定できます。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **Data Source**  
 ソースのデータ保存形式に対応したデータ プロバイダーを選択します。 データ ソースに使用できるプロバイダーが複数存在する可能性があります。 たとえば、で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、SQL Server の .NET Framework Data Provider、または SQL Server 用の Microsoft OLE DB プロバイダーを使用できます。  
  
 **データソース**プロパティには、コンピューターにインストールされているプロバイダーに応じて、さまざまなオプションがあります。 次の表に、使用頻度の高いプロバイダーのオプションを一覧表示します。 他のプロバイダーについては、プロバイダー固有のマニュアルを参照してください。  
  
## <a name="dynamic-options"></a>動的オプション  
 以下では、いくつかのデータ ソースで利用可能なオプションを示します。 [データ ソース] のドロップダウンで利用可能なすべてのデータ ソースが、ここに一覧表示されているわけではありません。  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a>[データ ソース] = [SQL Server Native Client] および [Microsoft OLE DB Provider for SQL Server]  
 **サーバー名**  
 データが格納されているサーバーの名前を入力するか、一覧からサーバーを選択します。  
  
 **Windows 認証を使用する**  
 データベースへのログインに、パッケージが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するかどうかを指定します。 より高いセキュリティのためには Windows 認証をお勧めします。  
  
 **SQL Server 認証を使用する**  
 データベースへのログインに、パッケージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するかどうかを指定します。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。  
  
 **ユーザー名**  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。  
  
 **パスワード**  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。  
  
 **[データベース]**  
 指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベースの一覧から選択します。  
  
 **[更新]**  
 
  **[更新]** をクリックして、利用可能なデータベースの一覧を復元します。  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a>[データ ソース] = [.Net Framework Data Provider for SQL Server]  
 このページでは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ プロバイダーのオプションがアルファベット順で一覧表示されます。 最も重要なオプションを次の表に示します。  
  
 **Data Source**  
 データが格納されているサーバーの名前を入力するか、一覧からサーバーを選択します。  
  
 **初期カタログ**  
 ソース データベース名を入力します。  
  
 **統合セキュリティ**  
 
  `True` を指定して Windows 統合認証を使用して接続するか (推奨)、`False` を指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続します。 
  `False` を指定した場合は、ユーザー ID とパスワードを入力する必要があります。 既定値は `False` です。  
  
 **User ID**  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。  
  
 **パスワード**  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。  
  
 このプロバイダーを選択したときに一覧表示される追加オプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のソース データベースに正しく接続するために必須というわけではありません。 これらの追加オプションの説明については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ソフトウェア開発キットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Provider for [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] のマニュアルを参照してください。  
  
### <a name="data-source--microsoft-excel"></a>[データ ソース] = [Microsoft Excel]  
  
> [!NOTE]  
>  Excel 2003 以前を使用しているデータソースに接続する場合にのみ、[ **Microsoft Excel** ] を選択します。 Excel 2007 を使用するデータソースに接続するには、[ **Microsoft Office 12.0 Access データベースエンジン OLE DB プロバイダー**] を選択し、[**プロパティ**] をクリックします。次に、[ `Excel 12.0` **データリンクプロパティ**] ダイアログボックスの [**すべて**] タブで、**拡張プロパティ**の値として「」と入力します。  
  
 **[Excel ファイル パス]**  
 データをインポートするスプレッドシートのパスとファイル名を指定します。 たとえば、 **C:\MyData.xls、 \\\Sales\Database\Northwind.xls**のようになります。 または、**[参照]** をクリックします。  
  
 **[参照]**  
 
  **[ファイルを開く]** ダイアログ ボックスを使用して、ワークシートを検索します。  
  
 **[Excel バージョン]**  
 ソース データが格納されている Excel のバージョンを選択します。  
  
> [!NOTE]  
>  ウィザードでは、データを [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ソースからインポートするときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel ソース コンポーネントを使用します。 使用に関する注意点と既知の問題については、「[Excel ソース](../data-flow/excel-source.md)」を参照してください。  
  
### <a name="data-source--microsoft-access"></a>[データ ソース] = [Microsoft Access]  
  
> [!NOTE]  
>  Access 2003 以前を使用しているデータベースに接続する場合にのみ、[ **Microsoft access** ] を選択します。 Access 2007 を使用するデータベースに接続するには、代わりに [ **Microsoft Office 12.0 access データベースエンジン OLE DB プロバイダー** ] を選択します。  
  
 **ファイル名**  
 データをインポートするデータベース ファイルのパスとファイル名を指定します。 たとえば、**C:\MyData.mdb、\\\Sales\Database\Northwind.mdb** などです。 または、**[参照]** をクリックします。  
  
 **[参照]**  
 
  **[ファイルを開く]** ダイアログ ボックスを使用して、データベース ファイルを検索します。  
  
 **ユーザー名**  
 ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のために有効なユーザー名を指定します。  
  
 **パスワード**  
 ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のためにユーザーのパスワードを指定します。 ただし、データベースがすべてのユーザーに対して1つのパスワードで保護されている場合は、[**データリンクプロパティ**] ダイアログボックスでこの値を指定する必要があります。このダイアログボックスにアクセスするには、[**詳細設定**] をクリックします。  
  
 **詳細設定**  
 [**データリンクプロパティ**] ダイアログボックスを使用して、データベースパスワードや既定以外のワークグループ情報ファイルなどの詳細オプションを指定することもできます。 OLE DB プロバイダーのプロパティの詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/?linkid=62553)の「データアクセス」セクションを検索してください。  
  
### <a name="data-source--flat-file-source"></a>[データ ソース] = [フラット ファイル ソース]  
 フラット ファイル ソースのオプションの詳細については、次のトピックを参照してください。  
  
 [[フラットファイル接続マネージャーエディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)  
  
 [[フラットファイル接続マネージャーエディター &#40;列] ページ&#41;](../flat-file-connection-manager-editor-columns-page.md)  
  
 [[フラットファイル接続マネージャーエディター] &#40;[詳細設定] ページ&#41;](../flat-file-connection-manager-editor-advanced-page.md)  
  
 [フラットファイル接続マネージャーエディター &#40;プレビューページ&#41;](../flat-file-connection-manager-editor-preview-page.md)  
  
  
