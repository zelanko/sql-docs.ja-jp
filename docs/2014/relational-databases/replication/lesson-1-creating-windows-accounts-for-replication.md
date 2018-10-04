---
title: 'レッスン 1 : レプリケーション用の Windows アカウントの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 0269a82d4ef11e53c41d7b288797064e0f3abd16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095572"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>レッスン 1 : レプリケーション用の Windows アカウントの作成
  このレッスンでは、レプリケーション エージェントを実行するための Windows アカウントを作成します。 また、次のエージェントを実行するための別の Windows アカウントをローカル サーバー上に作成します。  
  
|エージェント|場所|アカウント名|  
|-----------|--------------|------------------|  
|スナップショット エージェント|パブリッシャー|\<*machine_name*>\repl_snapshot|  
|ログ リーダー エージェント (Log Reader Agent)|パブリッシャー|\<*machine_name*>\repl_logreader|  
|ディストリビューション エージェント|パブリッシャーおよびサブスクライバー|\<*machine_name*>\repl_distribution|  
|マージ エージェント|パブリッシャーおよびサブスクライバー|\<*machine_name*>\repl_merge|  
  
> [!NOTE]  
>  このレプリケーション チュートリアルでは、パブリッシャーとディストリビューターで同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有します。 パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。 パブリッシャーとサブスクライバーが同じインスタンスを共有している場合、サブスクライバー側でアカウントの作成に使用される手順は必要ありません。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>パブリッシャー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには  
  
1.  パブリッシャー側で、[コントロール パネル] の **[管理ツール]** から **[コンピューターの管理]** を開きます。  
  
2.  **[システム ツール]** の **[ローカル ユーザーとグループ]** を展開します。  
  
3.  **[ユーザー]** を右クリックし、 **[新しいユーザー]** をクリックします。  
  
4.  入力`repl_snapshot`で、**ユーザー名**ボックスで、パスワード、およびその他の関連する情報を提供し をクリックし、**作成**して repl_snapshot アカウントを作成します。  
  
5.  同様に、repl_logreader、repl_distribution、repl_merge の各アカウントを作成します。  
  
6.  **[閉じる]** をクリックします。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>サブスクライバー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには  
  
1.  サブスクライバー側で、[コントロール パネル] の **[管理ツール]** から **[コンピューターの管理]** を開きます。  
  
2.  **[システム ツール]** の **[ローカル ユーザーとグループ]** を展開します。  
  
3.  **[ユーザー]** を右クリックし、 **[新しいユーザー]** をクリックします。  
  
4.  入力`repl_distribution`で、**ユーザー名**ボックスで、パスワード、およびその他の関連する情報を提供し をクリックし、**作成**repl_distribution アカウントを作成します。  
  
5.  同様にして、repl_merge アカウントも作成します。  
  
6.  **[閉じる]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、レプリケーション エージェントを実行するための Windows アカウントを作成しました。 次はスナップショット フォルダーを設定します。 「 [レッスン 2: スナップショット フォルダーの準備](lesson-2-preparing-the-snapshot-folder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの概要](agents/replication-agents-overview.md)  
  
  
