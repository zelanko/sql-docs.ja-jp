---
title: "ポリシー ベースの管理ポリシーのエクスポート | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c409fd3fc46ce2612290737bf658dd4358280495
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="export-a-policy-based-management-policy"></a>ポリシー ベースの管理ポリシーのエクスポート
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシーをエクスポートする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してポリシーをエクスポートするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-export-a-policy"></a>ポリシーをエクスポートするには  
  
1.  オブジェクト エクスプローラーで、エクスポートするポリシー ベースの管理ポリシーを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]**を展開します。  
  
4.  プラス記号をクリックして **[ポリシー]** フォルダーを展開します。  
  
5.  エクスポートするポリシーを右クリックし、 **[ポリシーのエクスポート]**をクリックします。  
  
6.  **[ポリシーのエクスポート]** ダイアログ ボックスで、アドレス バーにファイルのパスと名前を入力します。 または、ダイアログ ボックスのナビゲーション ウィンドウでファイルの適切な場所を見つけ、 **[ファイル名]** ボックスに XML ファイルの名前を入力します。  
  
7.  完了したら、 **[保存]**をクリックします。  
  
  
