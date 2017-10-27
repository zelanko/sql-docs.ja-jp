---
title: "バックアップし、復元の Reporting Services SharePoint サービス アプリケーションの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: b6dcd64d6f9662ae592474053e6cc9bbce53a83e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="back-up-and-restore-reporting-services-sharepoint-service-applications"></a>バックアップおよび Reporting Services SharePoint サービス アプリケーションを復元します。

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

このトピックをバックアップおよび復元する方法について説明、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーションが SharePoint サーバーの全体管理または PowerShell を使用します。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

## <a name="before-you-begin"></a>アンインストールの準備

### <a name="limitations-and-restrictions"></a>制限事項と制約事項

> [!NOTE]
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーションは部分的にバックアップおよび復元バックアップおよび復元機能、SharePoint を使用します。 これには**追加の手順が必要** であり、その手順はこのトピック内に記載されています。 バックアップ プロセスでは現在**しない**暗号化キーおよび無人実行アカウント (UEA) または windows 認証の資格情報をバックアップ、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]データベース。

### <a name="recommendations"></a>推奨事項
  
-   SharePoint のバックアップを開始する前に暗号化キーをバックアップします。 場合は、暗号化キーをバックアップできませんしないことができます、暗号化されたデータにアクセスする次のサービス アプリケーションの復元します。 その場合、暗号化されたデータを削除する必要が生じます。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションがデータベースへのアクセス用に UEA または Windows 認証を使用しているかどうかを確認してください。 これらのいずれかを使用している場合は、復元プロセス後にサービス アプリケーションを正しく構成できるよう、適切な資格情報を確認してください。  
  
-   SharePoint のバックアップ ログがバックアップ ファイルと同じフォルダーに作成されたことを確認します。 このファイルは通常、 **spbackup.log**という名前になります。  
  
## <a name="back-up-the-service-application"></a>サービス アプリケーションをバックアップします。

 次の手順を実行します。  
  
1.  暗号化キーをバックアップします。  
  
2.  サービス アプリケーションをバックアップします。  
  
3.  サービス アプリケーションがデータベースへのアクセス用に UEA または Windows 認証を使用しているかどうかを確認します。 使用している場合は、復元後にサービス アプリケーションを正しく構成できるよう、必要な資格情報をメモします。  

### <a name="back-up-the-encryption-keys-using-sharepoint-central-administration"></a>SharePoint サーバーの全体管理を使用して暗号化キーのバックアップします。

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 暗号化キーをバックアップする方法の詳細については、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)」の「暗号化キー」セクションを参照してください。  

### <a name="back-up-the-service-application-using-sharepoint-central-administration"></a>SharePoint サーバーの全体管理を使用してサービス アプリケーションをバックアップします。

サービス アプリケーションをバックアップするには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理の選択 で**バックアップを実行**で、**のバックアップし、復元**グループ。  
  
2.  **[共有サービス]** ノードで、 **[共有サービス アプリケーション]** を展開し、サービス アプリケーションを選択します。 種類は **[SQL Server Reporting Services サービス アプリケーション]**になります。  
  
3.  **[次へ]** を選択します。  
  
4.  パスを入力、**バックアップの場所:**選択**バックアップの開始**  
  
5.  上記のプロセスを繰り返します。ただし、サービス アプリケーションを選択する代わりに、 **[共有サービス プロキシ]** ノードを展開し、サービス アプリケーション プロキシを選択します。 種類は **[SQL Server Reporting Services サービス アプリケーション プロキシ]**になります。  
  
 詳細については、 SharePoint のドキュメントの次のトピックを参照してください。  
  
 [サービス アプリケーションのバックアップ (SharePoint Foundation 2010) (SharePoint ドキュメント)](http://msdn.microsoft.com/library/ee748601.aspx)。  
  
 [サービス アプリケーションのバックアップ (SharePoint Server 2010)](http://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a>実行アカウントとデータベース認証を確認してください。

 **実行アカウント** : サービス アプリケーションが実行アカウントを使用しているかどうかを確認するには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で、次のように選択します。**サービス アプリケーションの管理**で、**アプリケーション管理**グループ。  
  
2.  サービス アプリケーションの名前を選択し、**管理**SharePoint リボンでします。  
  
3.  選択**実行アカウント**です。  
  
4.  実行アカウントが構成されている場合は、サービス アプリケーションのバックアップを復元する際に資格情報が必要になります。 必ず、正しい資格情報を確認してからバックアップおよび復元の手順に進んでください。  
  
 **データベース認証** : サービス アプリケーションがデータベース認証用に Windows 認証を使用しているかどうかを確認するには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で、次のように選択します。**サービス アプリケーションの管理**で、**アプリケーション管理**グループ。  
  
2.  サービス アプリケーションの名前を選択し、**プロパティ**SharePoint リボンでします。  
  
3.  **[Reporting Services (SSRS) サービス データベース]** セクションの内容を確認します。  
  
4.  Windows 認証が構成されている場合は、サービス アプリケーションを復元後に構成する際、資格情報が必要になります。 必ず、正しい資格情報を確認してからバックアップおよび復元の手順に進んでください。  
  
## <a name="restore-the-service-application"></a>サービス アプリケーションを復元します。

 次の手順を実行します。  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを復元します。  
  
2.  暗号化キーを復元します。  
  
3.  サービス アプリケーションがデータベースへのアクセス用に実行アカウントまたは Windows 認証を使用していた場合は、資格情報を構成します。  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a>SharePoint サーバーの全体管理を使用してサービス アプリケーションを復元します。
  
1.  SharePoint サーバーの全体管理の選択 で**バックアップから復元**で、**のバックアップし、復元**グループ。  
  
2.  バックアップ ファイルへのパスを入力**バックアップ ディレクトリの場所**ボックスし、選択**更新**です。  
  
3.  サービス アプリケーションのバックアップを選択して、**トップ コンポーネント**を一覧表示し、**次**です。  
  
4.  選択、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アプリケーションを選択し、**次**です。  
  
5.  **[ログイン名とパスワード]** セクションで、ログイン名のパスワードを入力します。 サービス アプリケーションは、バックアップする前を使用していたログインを持つログイン名 ボックスが取り込まれます。  
  
6.  選択**復元を開始**です。  
  
7.  上記のプロセスを繰り返します。ただし、サービス アプリケーションを復元する代わりに、 **[共有サービス]** ノードを展開し、 **[共有サービス アプリケーション]** ノードを展開します。  
  
 詳細については、 SharePoint のドキュメントの次のトピックを参照してください。  
  
 [サービス アプリケーションを復元する (SharePoint Foundation 2010)](http://msdn.microsoft.com/library/ee748615.aspx)。  
  
 [サービス アプリケーションを復元する (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx)。  

### <a name="restore-the-encryption-keys-using-sharepoint-central-administration"></a>SharePoint サーバーの全体管理を使用して暗号化キーを復元します。

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 暗号化キーを復元する方法の詳細については、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)」の「暗号化キー」セクションを参照してください。  

### <a name="configure-the-execution-account-and-database-authentication"></a>実行アカウントとデータベース認証を構成します。

 **実行アカウント** : サービス アプリケーションが実行アカウントを使用していた場合は、次の手順を実行して実行アカウントを構成します。  
  
1.  SharePoint サーバーの全体管理で、次のように選択します。**サービス アプリケーションの管理**で、**アプリケーション管理**グループ。  
  
2.  サービス アプリケーションの名前を選択し、**管理**SharePoint リボンでします。  
  
3.  選択**実行アカウント**です。  
  
4.  アカウントとパスワードを入力し、 **[実行アカウントの指定]** ボックスを選択します。  
  
5.  [ **OK**] を選択します。  
  
 **データベース認証** : サービス アプリケーションがデータベース認証用に Windows 認証を使用していた場合は、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理の選択で**サービス アプリケーションの管理**で、**アプリケーション管理**グループ。  
  
2.  サービス アプリケーションの名前を選択し、**プロパティ**SharePoint リボンでします。  
  
3.  **[Reporting Services (SSRS) サービス データベース]** セクションの内容を確認します。  
  
4.  **[Windows 認証]**をクリックします。  
  
5.  アカウントとパスワードを入力します。 必要に応じて、 **[Windows 資格情報として使用する]** を選択します。  
  
6.  選択**Ok**

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

