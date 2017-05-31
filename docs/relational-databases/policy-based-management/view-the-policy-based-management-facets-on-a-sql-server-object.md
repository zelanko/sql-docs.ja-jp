---
title: "SQL Server オブジェクトのポリシー ベースの管理ファセットの表示 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 79cdef304ef11e7d8f58b922e1ed924afb3eb1fa
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>SQL Server オブジェクトのポリシー ベースの管理ファセットの表示
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で特定の SQL Server オブジェクトに適用されているすべてのポリシー ベースの管理ファセットを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してオブジェクトのすべてのファセットを表示するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>オブジェクトのすべてのファセットを表示するには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]**をクリックします。  
  
2.  **[ファセットの表示 -***オブジェクト名* ] ダイアログ ボックスの **[ファセット]** ボックスの一覧で、プロパティを表示するファセットを選択します。 このダイアログ ボックスで利用可能なオプションの詳細については、「 [View Facets Dialog Box](../../relational-databases/policy-based-management/view-facets-dialog-box.md)」を参照してください。  
  
3.  完了したら、 **[OK]**をクリックします。  
  
  
