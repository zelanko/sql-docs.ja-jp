---
title: "Power Pivot の最小限の特権の例 - SharePoint 2016 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35757f68-7bfc-4906-a985-f369690b9237
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae8b2b882204fa6940a5e4827ca3a5a0b1344dbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="power-pivot-minimum-privilege-example---sharepoint-2016"></a>Power Pivot の最小限の特権の例 - SharePoint 2016
  このトピックでは、最小限の特権を使用する [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 構成の例について説明します。 この構成では、3 種類のコンポーネントごとに個別のアカウントを使用します。各アカウントには最小レベルの特権を指定します。  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2016|  
  
## <a name="summary-of-accounts"></a>アカウントの概要  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 では、Analysis Services サービス アカウントに Network Service アカウントを使用できます。 Network Service アカウントは、SharePoint 2010 のシナリオではサポートされません。 サービス アカウントの詳細については、「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/library/ms143504.aspx) 」(http://msdn.microsoft.com/library/ms143504.aspx) を参照してください。  
  
 次の表は、最小限の特権の構成の例で使用する 3 種類のアカウントをまとめたものです。  
  
|スコープ|名前|  
|-----------|----------|  
|SharePoint 管理者アカウント|**SPAdmin**|  
|SharePoint ファーム アカウント|**SPFarm**|  
|Analysis Services サービス アカウント|**SPsvc**|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a>SharePoint 管理者アカウント (SpAdmin)  
 **SPAdmin** は、ファームのインストールと構成に使用するドメイン アカウントです。 このアカウントは、SharePoint 構成ウィザードと SharePoint 2016 用 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールの実行に使用します。 **SPAdmin** は、ローカル管理者権限が必要になる唯一のアカウントです。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールを実行する前に、 **SPAdmin** アカウントの特権を、SharePoint によってコンテンツ データベースと構成データベースが作成される SQL Server データベース インスタンスに与えます。 最小限の特権のシナリオで SPAdmin アカウントを構成する場合、SPAdmin アカウントは **securityadmin** ロールと **dbcreator**ロールのメンバーにします。  
  
### <a name="the-farm-account-spfarm"></a>ファーム アカウント (SPFarm)  
 **SPFarm** は、SharePoint Timer Service と全体管理用 Web アプリケーションが SharePoint コンテンツ データベースにアクセスするために使用するドメイン アカウントです。 このアカウントは、ローカル管理者である必要はありません。 SharePoint 構成ウィザードでは、バックエンドの SQL Server データベースで必要最小限の特権を付与します。SQL Server の特権の最小限の構成は **securityadmin** ロールと **dbcreator**ロールのメンバーシップです。  
  
### <a name="the-service-account-for-power-pivot-service-spsvc"></a>PowerPivot サービスのサービス アカウント (SPsvc)  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールを実行する前に新しい SharePoint ファームが構成されていない場合、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールでは既定で以下のものを作成します。  
  
-   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Service アプリケーション。  
  
-   Secure Store アプリケーション。  
  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールは、既定のアプリケーション プールの両方のサービス アプリケーションを構成します。 アプリケーション プールは、通常 SPFarm アカウントで実行するように構成されます。このアカウントはサービス アカウントが必要としない多くのリソースにアクセスします。 最小限の特権環境にするには、適切なアプリケーション プールと Web アプリケーションで使用される新しいドメイン アカウントを構成します。  
  
 **SharePoint Service アカウントとして使用する新しいドメイン アカウント SPsvc を作成するには**  
  
1.  SharePoint のサーバーの全体管理で **[セキュリティ]**を選択します。  
  
2.  **[サービス アカウントの構成]**を選択します。  
  
3.  **[新しい管理アカウントの登録]**を選択します。  
  
 **SPSvc** アカウントにはローカル管理者権限はなく、SharePoint データベースに関する権限もありません。 SPsvc に必要な唯一の特権は、Analysis Services の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] インスタンスの管理権限です。  
  
 **SPsvc アカウントを使用する適切なアプリケーション プールを構成するには**  
  
1.  SharePoint のサーバーの全体管理で **[セキュリティ]**を選択します。  
  
2.  **[サービス アカウントの構成]**を選択します。  
  
3.  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーションで使用するサービス アプリケーション プールを選択します。 次に、SPSvc アカウントを選択します。  
  
 **PowerShell で Web アプリケーションへのアクセス権を付与するには**  
  
1.  管理者特権を使用して、SharePoint 2016 管理シェルを実行します。  
  
2.  次の PowerShell コードを実行します。  
  
    ```  
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")  
  
    ```  
  
  
