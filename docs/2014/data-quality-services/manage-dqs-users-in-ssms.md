---
title: SSMS で DQS ユーザーを管理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: eccb3ea2ec046a84a2735c310c8b80c5e88cf96e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480352"
---
# <a name="manage-dqs-users-in-ssms"></a>SSMS による DQS ユーザーの管理
  このトピックでは、SQL Server Management Studio を使用して SQL Server インスタンスで追加のユーザーを作成し、DQS_MAIN データベースの適切な [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ロールを付与する方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 SQL ログインを作成し、適切な DQS ロールを付与するには、Windows ユーザー アカウントが適切な固定サーバー ロール (securityadmin、serveradmin、sysadmin など) のメンバーであることが必要です。  
  
##  <a name="GrantRoles"></a>SQL ログインを作成し、DQS ロールを付与する  
  
1.  Microsoft SQL Server Management Studio を起動します。  
  
2.  Microsoft SQL Server Management Studio で、SQL Server インスタンスを展開し、 **[セキュリティ]** を展開します。  
  
3.  
  **[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[ログイン]** をクリックします。  
  
4.  
  **[ログイン - 新規作成]** ダイアログ ボックスの **[ログイン名]** ボックスで Windows ユーザーの名前を指定し、認証の種類として **[Windows 認証]** を指定し、**[検索]** をクリックしてユーザーを検証します。  
  
    > [!NOTE]  
    >  DQS では、Windows 認証のみサポートします。SQL Server 認証はサポートされていません。  
  
5.  ユーザーの検証後、左ペインの **[ユーザー マッピング]** ページをクリックします。  
  
6.  右ペインで、 **[DQS_MAIN]** データベースの **[マップ]** 列のチェック ボックスをオンにし、ユーザーに必要なアクセス レベルに応じて、 **[DQS_MAIN のデータベース ロール メンバーシップ]** ペインで **[dqs_administrator]**、 **[dqs_kb_editor]** 、または **[dqs_kb_operator]** チェック ボックスをオンにします。  
  
7.  
  **[ログイン - 新規作成]** ダイアログ ボックスで、**[OK]** をクリックして変更を適用します。  
  
    > [!NOTE]  
    >  
  **dqs_administrator** ロールをユーザーに付与し、変更を適用してから、ユーザー権限を再びオンにすると、その他の 2 つの DQS ロールのチェック ボックス (**[dq_kb_editor]** および **[dqs_kb_operator]**) もオンになります。  
  
  
