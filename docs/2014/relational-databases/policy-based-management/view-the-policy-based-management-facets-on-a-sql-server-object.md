---
title: SQL Server オブジェクトのポリシー ベースの管理ファセットの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b49882abc1e9cdd43a51cd702a33500131793000
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85038390"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>SQL Server オブジェクトのポリシー ベースの管理ファセットの表示
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で特定の SQL Server オブジェクトに適用されているすべてのポリシー ベースの管理ファセットを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **以下を使用してオブジェクトのすべてのファセットを表示するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>オブジェクトのすべてのファセットを表示するには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]** をクリックします。  
  
2.  [ファ**セットの表示-**_object_name_ ] ダイアログボックスの [**ファセット**] ボックスの一覧で、プロパティを表示するファセットを選択します。 このダイアログ ボックスで利用可能なオプションの詳細については、「 [View Facets Dialog Box](view-facets-dialog-box.md)」を参照してください。  
  
3.  完了したら、[**OK**] をクリックします。  
  
  
