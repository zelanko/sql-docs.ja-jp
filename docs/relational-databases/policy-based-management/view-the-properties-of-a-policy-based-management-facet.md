---
title: ポリシー ベースの管理ファセットのプロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bc6e7858a757ed24e25adf11cff45d842cf9a47b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>ポリシー ベースの管理ファセットのプロパティの表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ファセットのプロパティを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **以下を使用してファセットのプロパティを表示するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-the-properties-of-a-facet"></a>ファセットのプロパティを表示するには  
  
1.  **オブジェクト エクスプローラー**で、プロパティを表示するファセットを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]** を展開します。  
  
4.  プラス記号をクリックして **[ファセット]** フォルダーを展開します。  
  
5.  プロパティを表示するファセットを右クリックし、 **[プロパティ]** をクリックします。 *[ファセットのプロパティ - <ファセット名>]* ダイアログ ボックスで使用可能なオプションの詳細については、「[[ファセットのプロパティ] ダイアログ ボックスの [全般] ページ](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md)」、「[[ファセットのプロパティ] ダイアログ ボックスの [依存ポリシー] ページ](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md)」、「[[ファセットのプロパティ] ダイアログ ボックスの [依存条件] ページ](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md)」をご覧ください。  
  
6.  完了したら、 **[閉じる]** をクリックします。  
  
  
