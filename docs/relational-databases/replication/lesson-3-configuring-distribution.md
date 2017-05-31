---
title: "レッスン 3 : ディストリビューションの構成 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e582c5fb7853c69a083755a944bd3922d0d4c5af
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-3-configuring-distribution"></a>レッスン 3 : ディストリビューションの構成
このレッスンでは、パブリッシャー側のディストリビューションを構成し、パブリケーション データベースとディストリビューション データベースに対して必要な権限を設定します。 ディストリビューターを構成済みの場合は、このレッスンを開始する前に、パブリッシングとディストリビューションを無効にする必要があります。 既存のレプリケーション トポロジを維持する必要がある場合は、このレッスンを実行しないでください。  
  
パブリッシャー側のリモート ディストリビューターの構成は、このチュートリアルの対象外です。  
  
### <a name="configuring-distribution-at-the-publisher"></a>パブリッシャー側のディストリビューションを構成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを右クリックし、 **[ディストリビューションの構成]**をクリックします。  
  
    > [!NOTE]  
    > 実際のサーバー名ではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localhost **を使用して** に接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が **'localhost'**サーバーに接続できないことを示す警告とメッセージが表示されます。 警告ダイアログで **[OK]** をクリックします。 **[サーバーへの接続]** ダイアログで、 **[サーバー名]** を **localhost** から使用しているサーバーの名前に変更します。 **[接続]**をクリックします。  
  
    ディストリビューション構成ウィザードが起動します。  
  
3.  **[ディストリビューター]** ページで、['&lt;サーバー名&gt;' を独自のディストリビューターとする (SQL Server はディストリビューション データベースとログを作成します)]を選択し、**[次へ]** をクリックします。  
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていない場合は、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントの起動** ] ページで **[はい]**を選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが自動的に起動するように構成します。 **[次へ]**をクリックします。  
  
5.  **[スナップショット フォルダー]** ボックスに、「**\\\\**\<*コンピューター名>***\repldata**」と入力します (\<*コンピューター名>* はパブリッシャーの名前)。その後、**[次へ]** をクリックします。  
  
6.  ウィザードの残りのページでは、既定値をそのまま使用します。  
  
7.  **[完了]** をクリックしてディストリビューションを有効にします。  
  
### <a name="setting-database-permissions-at-the-publisher"></a>パブリッシャー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[セキュリティ]**を展開して **[ログイン]**を右クリックし、 **[新しいログイン]**をクリックします。  
  
2.  **[全般]** ページで、**[検索]** をクリックして **[選択するオブジェクト名を入力してください]** ボックスに「\<*コンピューター名>***\repl_snapshot**」と入力します (\<*コンピューター名>* はローカルのパブリッシャー サーバーの名前)。その後、**[名前の確認]** をクリックし、**[OK]** をクリックします。  
  
3.  **[このログインにマップされたユーザー]** の一覧にある **[ユーザー マッピング]** ページで、 **ディストリビューション** データベースと [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの両方を選択します。  
  
    **[データベース ロールのメンバーシップ]** の一覧で、両方のデータベースのログイン用に **db_owner** ロールを選択します。  
  
4.  **[OK]** をクリックすると、ログインが作成されます。  
  
5.  手順 1. ～ 4. を繰り返して、ローカルの repl_logreader アカウントのログインを作成します。 このログインも、 **ディストリビューション** データベースと **AdventureWorks** データベースの固定データベース ロール **db_owner** のメンバーとなっているユーザーにマップする必要があります。  
  
6.  手順 1. ～ 4. を繰り返して、ローカルの repl_distribution アカウントのログインを作成します。 このログインは、 **ディストリビューション** データベースの固定データベース ロール **db_owner** のメンバーとなっているユーザーにマップする必要があります。  
  
7.  手順 1. ～ 4. を繰り返して、ローカルの repl_merge アカウントのログインを作成します。 このログインは、 **ディストリビューション** データベースと **AdventureWorks** データベースのユーザーにマップする必要があります。  
  
## <a name="see-also"></a>参照  
[[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)  
[レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)  
  
  
  

