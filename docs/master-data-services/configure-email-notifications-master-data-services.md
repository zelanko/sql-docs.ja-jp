---
title: "電子メール通知を構成する (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "電子メール [マスター データ サービス], 構成"
  - "通知 [マスター データ サービス], 通知の構成"
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# 電子メール通知を構成する (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で電子メール メッセージを自動的に送信する場合は、通知電子メールを構成します。  
  
### 通知を構成するには  
  
1.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の **[データベース]** ページで、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択します。  
  
2.  **[システム設定]** セクションで、**[プロファイルの作成]** をクリックします。  
  
3.  すべての必須フィールドを入力します。 詳細については、「[[データベース メール プロファイルとアカウントの作成] ダイアログ ボックス (マスター データ サービス構成マネージャー)](../Topic/Create%20Database%20Mail%20Profile%20and%20Account%20Dialog%20Box%20\(Master%20Data%20Services%20Configuration%20Manager\).md)」を参照してください。  
  
4.  **[OK]**をクリックします。  
  
    > [!NOTE]  
    >  通知を構成した後に [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]を使用して変更を加えることはできません。 変更は [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで直接行う必要があります。 詳細については、「[データベース メール構成オブジェクト](../relational-databases/database-mail/database-mail-configuration-objects.md)」を参照してください。  
  
## 次の手順  
  
-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、通知に影響を与える設定があります。 これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するか、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの System Settings テーブルで直接調整することができます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## 参照  
 [通知 (マスター データ サービス)](../master-data-services/notifications-master-data-services.md)   
 [電子メール通知のトラブルシューティング (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)   
 [通知を送信するようにビジネス ルールを構成する (マスター データ サービス)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  