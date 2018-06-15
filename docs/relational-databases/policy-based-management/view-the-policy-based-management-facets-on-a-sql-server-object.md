---
title: SQL Server オブジェクトのポリシー ベースの管理ファセットの表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 860ffb36a0a4a51f5f4a3076abcabc193f56e081
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32953197"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>SQL Server オブジェクトのポリシー ベースの管理ファセットの表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で特定の SQL Server オブジェクトに適用されているすべてのポリシー ベースの管理ファセットを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **以下を使用してオブジェクトのすべてのファセットを表示するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>オブジェクトのすべてのファセットを表示するには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]** をクリックします。  
  
2.  *[ファセットの表示 - <オブジェクト名>]* ダイアログ ボックスの **[ファセット]** ボックスの一覧で、プロパティを表示するファセットを選択します。 このダイアログ ボックスで利用可能なオプションの詳細については、「 [View Facets Dialog Box](../../relational-databases/policy-based-management/view-facets-dialog-box.md)」を参照してください。  
  
3.  完了したら、 **[OK]** をクリックします。  
  
  
