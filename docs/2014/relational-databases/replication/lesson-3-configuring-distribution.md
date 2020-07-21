---
title: 'レッスン 3 : ディストリビューションの構成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 28df67dad52bcd11a18fc5deb42a6725700dde5a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065945"
---
# <a name="lesson-3-configuring-distribution"></a>レッスン 3 : ディストリビューションの構成
  このレッスンでは、パブリッシャー側のディストリビューションを構成し、パブリケーション データベースとディストリビューション データベースに対して必要な権限を設定します。 ディストリビューターを構成済みの場合は、このレッスンを開始する前に、パブリッシングとディストリビューションを無効にする必要があります。 既存のレプリケーション トポロジを維持する必要がある場合は、このレッスンを実行しないでください。  
  
 パブリッシャー側のリモート ディストリビューターの構成は、このチュートリアルの対象外です。  
  
### <a name="configuring-distribution-at-the-publisher"></a>パブリッシャー側のディストリビューションを構成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを右クリックし、 **[ディストリビューションの構成]** をクリックします。  
  
    > [!NOTE]  
    >  実際のサーバー名ではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localhost **を使用して** に接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が **'localhost'** サーバーに接続できないことを示す警告とメッセージが表示されます。 警告ダイアログで **[OK]** をクリックします。 **[サーバーへの接続]** ダイアログで、 **[サーバー名]** を **localhost** から使用しているサーバーの名前に変更します。 **[Connect]** をクリックします。  
  
     ディストリビューション構成ウィザードが起動します。  
  
3.  [**ディストリビューター** ] ページで、[' ' を **'** _\<ServerName>_ **独自のディストリビューターとして動作させる] を選択します。SQL Server によってディストリビューションデータベースとログが作成され**、[**次へ**] をクリックします。  
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていない場合は、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントの起動** ] ページで **[はい]** を選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが自動的に起動するように構成します。 **[次へ]** をクリックします。  
  
5.  [ **\\\\** \<_Machine_Name> **スナップショットフォルダー** ] テキストボックスに「_**\repldata」と**」と入力します。ここで、 \<*Machine_Name> * はパブリッシャーの名前です。次に、[**次へ**] をクリックします。  
  
6.  ウィザードの残りのページでは、既定値をそのまま使用します。  
  
7.  **[完了]** をクリックしてディストリビューションを有効にします。  
  
### <a name="setting-database-permissions-at-the-publisher"></a>パブリッシャー側のデータベース権限を設定するには  
  
1.  で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、[**セキュリティ**] を展開し、[**ログイン**] を右クリックして、[**新しいログイン**] を選択します。  
  
2.  [**全般**] ページで、[**検索**] をクリックし、[ \<_Machine_Name> **選択するオブジェクト名を入力**してください] ボックスに「_**\ repl_snapshot** 」と入力します。ここで、 \<*Machine_Name> * はローカルパブリッシャーサーバーの名前です。 [**名前の確認**] をクリックし、[ **OK**] をクリックします。  
  
3.  [**ユーザーマッピング**] ページの [**このログインにマップ**されたユーザー] ボックスの一覧で、**ディストリビューション**とデータベースの両方を選択し [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ます。  
  
     [**データベースロールのメンバーシップ**] ボックスの一覧で、 `db_owner` 両方のデータベースのログインのロールを選択します。  
  
4.  **[OK]** をクリックすると、ログインが作成されます。  
  
5.  手順 1. ～ 4. を繰り返して、ローカルの repl_logreader アカウントのログインを作成します。 このログインは `db_owner` 、**ディストリビューション**データベースと**AdventureWorks**データベースの固定データベースロールのメンバーであるユーザーにもマップする必要があります。  
  
6.  手順 1. ～ 4. を繰り返して、ローカルの repl_distribution アカウントのログインを作成します。 このログインは、 `db_owner` **ディストリビューション**データベースの固定データベースロールのメンバーであるユーザーにマップされている必要があります。  
  
7.  手順 1. ～ 4. を繰り返して、ローカルの repl_merge アカウントのログインを作成します。 このログインは、 **ディストリビューション** データベースと **AdventureWorks** データベースのユーザーにマップする必要があります。  
  
## <a name="see-also"></a>参照  
 [ディストリビューションの構成](configure-distribution.md)   
 [レプリケーションエージェントのセキュリティモデル](security/replication-agent-security-model.md)  
  
  
