---
title: "Reporting Services SharePoint サービスとサービス アプリケーションの管理 |Microsoft ドキュメント"
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
ms.openlocfilehash: 3b0351819369c0c17a5f97318b1132c69ec71432
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a>Reporting Services SharePoint サービスとサービス アプリケーション

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Reporting Services SharePoint モード、SharePoint サービス アーキテクチャ上に構築されており、SharePoint サービスと一対多のサービス アプリケーションを利用します。 サービス アプリケーションを作成すると、サービスが使用可能になり、サービス アプリケーション データベースが生成されます。 複数の Reporting Services サービス アプリケーションを作成することができますが、ほとんどの配置シナリオではサービス アプリケーションは 1 つで十分です。  

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。
  
## <a name="creating-a-reporting-services-service-application"></a>Reporting Services サービス アプリケーションを作成します。

 SharePoint サーバーの全体管理または PowerShell スクリプトを使用するには、Reporting Services サービス アプリケーションを作成します。 SharePoint サーバーの全体管理の使用に関する詳細についてを参照してください「Reporting Services サービス アプリケーションの作成」 [Install Reporting Services SharePoint Mode for SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c)です。 サービス アプリケーションを作成するための PowerShell スクリプトの例は、このトピックの後半の PowerShell のセクションを参照してください。  
  
## <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a>サービス アプリケーション プロキシ グループとの関連付けを変更します。

 サービス アプリケーションを作成するための [新規作成] ページには、 **[Web アプリケーションの関連付け]**セクションがあります。 このセクションでは、サービス アプリケーションの作成時に関連付けを行うことができます。 関連付けを変更してカスタム構成をサービス アプリケーションに割り当てるには、次の手順を使用します。 同じ一般的なプロセスは、サービス アプリケーションとカスタム グループとの関連付けを変更せずに、プロキシを既定のグループに追加する場合にも使用できます。  
  
1.  SharePoint サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの関連付けの構成]**をクリックします。  
  
2.  [サービス アプリケーションの関連付け] ページで、ビューを **[サービス アプリケーション]**に変更します。  
  
3.  検索し、新しい Reporting Services サービス アプリケーションの名前をクリックします。 アプリケーション プロキシ グループ名 **[既定]** をクリックして、次の手順を完了せずに、プロキシを既定のグループに追加することもできます。  
  
4.  **[編集する接続グループ]** 選択ボックスで、 **[カスタム]**をクリックします。  
  
5.  プロキシのチェック ボックスをオンにして、 **[OK]**をクリックします。  
  
## <a name="edit-service-application-properties"></a>サービス アプリケーション プロパティを編集します。

 サービス アプリケーションのプロパティ ページを開き直してプロパティを変更することができます。  
  
1.  SharePoint サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]**をクリックします。  
  
2.  サービス アプリケーションを選択するには、型列をクリックして行全体を選択します。 アプリケーションの名前をクリックすると、サービス アプリケーションのプロパティが開く代わりに、サービスの管理オプション ページが開きます。  
  
3.  [サービス アプリケーション] リボンで、 **[プロパティ]**をクリックします。  
  
## <a name="create-a-reporting-services-service-application-using-powershell"></a>PowerShell を使用して Reporting Services サービス アプリケーションを作成します。

 PowerShell を使用して Service アプリケーションとプロキシを作成することができます。 次のサンプルでは、使用するサービス アプリケーションをどのアプリケーション プールに構成するかがわかっていることを前提としています。  
  
1.  アプリケーション プール名のアプリケーション プール オブジェクトを、New アクションに渡される変数に追加します。  
  
    ```  
    $appPoolName = get-spserviceapplicationpool “<application pool name>”  
    ```  
  
2.  指定した名前とアプリケーション プール名を使用してサービス アプリケーションを作成します。  
  
    ```  
    New-SPRSServiceApplication –Name ‘MyServiceApplication’ –ApplicationPool $appPoolName –DatabaseName ‘MyServiceApplicationDatabase’ –DatabaseServer ‘<Server Name>’  
    ```  
  
3.  新しいサービス アプリケーション オブジェクトを取得し、新しいプロキシ コマンドレットにオブジェクトをパイプします。  
  
    ```  
    Get-SPRSServiceApplication –name MyServiceApplication | New-SPRSServiceApplicationProxy “MyServiceApplicationProxy”  
    ```  
  
## <a name="related-tasks"></a>関連タスク
  
|タスク|リンク|  
|----------|----------|  
|サービス アプリケーションの設定を管理する|[Manage a Reporting Services SharePoint Service Application](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)|  
|サービス アプリケーションと関連コンポーネント (暗号化キーやプロキシなど) をバックアップおよび復元する|[Reporting Services SharePoint サービス アプリケーションのバックアップと復元](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

