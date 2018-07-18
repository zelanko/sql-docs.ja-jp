---
title: データベース メールを使用するように SQL Server エージェント メールを構成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef40a0afa36d562fa46fa243bb2ab20fb82adf35
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318512"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>データベース メールを使用するように SQL Server エージェント メールを構成する
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の通知と警告をデータベース メールを使用して送信するように [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェントを構成する方法について説明します。  
  
-   **作業を開始する準備:**  
  
-   [前提条件](#Prerequisites)  
  
-   [Security](#Security)  
  
-   [SQL Server Management Studio でデータベース メールを使用するように SQL Server エージェントを構成するには](#SSMSProcedure)  
  
-   [フォロー アップ タスク](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   データベース メールを有効にします。  
  
-   使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのデータベース メール アカウントを作成します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのデータベース メール プロファイルを作成し、ユーザーを **msdb** データベースの **DatabaseMailUserRole** に追加します。  
  
-   作成したプロファイルを **msdb** データベースの既定のプロファイルに設定します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 プロファイル アカウントを作成し、ストアド プロシージャを実行するユーザーは、sysadmin 固定サーバー ロールのメンバーである必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **データベース メールを使用するように SQL Server エージェントを構成するには**  
  
-   オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを展開します。  
  
-   **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。  
  
-   **[警告システム]** をクリックします。  
  
-   **[メール プロファイルを有効にする]** チェック ボックスをオンにします。  
  
-   **[メール システム]** ボックスの一覧で、 **[データベース メール]** を選択します。  
  
-   **[メール プロファイル]** ボックスの一覧で、データベース メールのメール プロファイルを選択します。  
  
-   SQL Server エージェントを再起動します。  
  
##  <a name="Follow_Up"></a> フォロー アップ タスク  
 警告および通知を送信できるようにエージェントを構成するには、次のタスクが必要となります。  
  
-   [警告](../../ssms/agent/alerts.md)  
  
     特定のデータベース イベントまたはオペレーティング システムの状態がオペレーターに通知されるように、警告を構成できます。  
  
-   [演算子](../../ssms/agent/operators.md)  
  
     オペレーターとは、電子通知を受け取ることのできる人またはグループの別名です。  
  
  
