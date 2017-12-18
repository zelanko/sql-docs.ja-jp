---
title: "レッスン 1 : レプリケーション用の Windows アカウントの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9688b2bac34a38ea667557b997adfed3e7cf37d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>レッスン 1 : レプリケーション用の Windows アカウントの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このレッスンでは、レプリケーション エージェントを実行するための Windows アカウントを作成します。 また、次のエージェントを実行するための別の Windows アカウントをローカル サーバー上に作成します。  
  
|エージェント|場所|アカウント名|  
|---------|------------|----------------|  
|スナップショット エージェント|パブリッシャー|\<*machine_name*>\repl_snapshot|  
|ログ リーダー エージェント (Log Reader Agent)|パブリッシャー|\<*machine_name*>\repl_logreader|  
|ディストリビューション エージェント|パブリッシャーおよびサブスクライバー|\<*machine_name*>\repl_distribution|  
|マージ エージェント|パブリッシャーおよびサブスクライバー|\<*machine_name*>\repl_merge|  
  
> [!NOTE]  
> このレプリケーション チュートリアルでは、パブリッシャーとディストリビューターで同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有します。 パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。 パブリッシャーとサブスクライバーが同じインスタンスを共有している場合、サブスクライバー側でアカウントの作成に使用される手順は必要ありません。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>パブリッシャー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには  
  
1.  パブリッシャー側で、[コントロール パネル] の **[管理ツール]** から **[コンピューターの管理]** を開きます。  
  
2.  **[システム ツール]**の **[ローカル ユーザーとグループ]**を展開します。  
  
3.  **[ユーザー]** を右クリックし、 **[新しいユーザー]**をクリックします。  
  
4.  **[ユーザー名]** ボックスに「 **repl_snapshot** 」と入力し、パスワードおよびその他の必要な情報を入力し、 **[作成]** をクリックして repl_snapshot アカウントを作成します。  
  
5.  同様に、repl_logreader、repl_distribution、repl_merge の各アカウントを作成します。  
  
6.  **[閉じる]**をクリックします。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>サブスクライバー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには  
  
1.  サブスクライバー側で、[コントロール パネル] の **[管理ツール]** から **[コンピューターの管理]** を開きます。  
  
2.  **[システム ツール]**の **[ローカル ユーザーとグループ]**を展開します。  
  
3.  **[ユーザー]** を右クリックし、 **[新しいユーザー]**をクリックします。  
  
4.  **[ユーザー名]** ボックスに「 **repl_distribution** 」と入力し、パスワードおよびその他の必要な情報を入力し、 **[作成]** をクリックして repl_distribution アカウントを作成します。  
  
5.  同様にして、repl_merge アカウントも作成します。  
  
6.  **[閉じる]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
ここでは、レプリケーション エージェントを実行するための Windows アカウントを作成しました。 次はスナップショット フォルダーを設定します。 「 [レッスン 2: スナップショット フォルダーの準備](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
  
