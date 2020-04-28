---
title: データベース メールを使用するように SQL Server エージェント メールを構成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3c2f5f0be09e9a60997308efd72c360348efc60
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289210"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>データベース メールを使用するように SQL Server エージェント メールを構成する
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の通知と警告をデータベース メールを使用して送信するように [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェントを構成する方法について説明します。  
  
-   **作業を開始する準備:**  
  
-   [必要条件](#Prerequisites)  
  
-   [Security](#Security)  
  
-   [SQL Server Management Studio でデータベース メールを使用するように SQL Server エージェントを構成するには](#SSMSProcedure)  
  
-   [フォローアップタスク](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> 前提条件  
  
-   データベース メールを有効にします。  
  
-   使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのデータベース メール アカウントを作成します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのデータベース メール プロファイルを作成し、ユーザーを **msdb** データベースの **DatabaseMailUserRole** に追加します。  
  
-   作成したプロファイルを **msdb** データベースの既定のプロファイルに設定します。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 プロファイル アカウントを作成し、ストアド プロシージャを実行するユーザーは、sysadmin 固定サーバー ロールのメンバーである必要があります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **データベース メールを使用するように SQL Server エージェントを構成するには**  
  
-   オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを展開します。  
  
-   **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。  
  
-   **[警告システム]** をクリックします。  
  
-   **[メール プロファイルを有効にする]** チェック ボックスをオンにします。  
  
-   **[メール システム]** ボックスの一覧で、 **[データベース メール]** を選択します。  
  
-   **[メール プロファイル]** ボックスの一覧で、データベース メールのメール プロファイルを選択します。  
  
-   SQL Server エージェントを再起動します。  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> フォロー アップ タスク  
 警告および通知を送信できるようにエージェントを構成するには、次のタスクが必要となります。  
  
-   [アラート](../../ssms/agent/alerts.md)  
  
     特定のデータベース イベントまたはオペレーティング システムの状態がオペレーターに通知されるように、警告を構成できます。  
  
-   [演算子](../../ssms/agent/operators.md)  
  
     オペレーターとは、電子通知を受け取ることのできる人またはグループの別名です。  
  
  
