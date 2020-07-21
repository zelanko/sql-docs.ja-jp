---
title: 管理者以外のユーザーがレプリケーション モニターを使用できるようにする | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068651"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>管理者以外のユーザーがレプリケーション モニターを使用できるようにする
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、管理者以外のユーザーがレプリケーション モニターを使用できるようにする方法について説明します。 レプリケーション モニターは、次のロールのメンバーになっているユーザーが使用できます。  
  
-   **sysadmin** 固定サーバー ロール  
  
     これらのユーザーはレプリケーションを監視することができ、また、エージェント スケジュール、エージェント プロファイルなどのレプリケーション プロパティの変更に対するフル コントロール権限を持っています。  
  
-   `replmonitor`ディストリビューションデータベースのデータベースロールです。  
  
     これらのユーザーはレプリケーションを監視できますが、レプリケーション プロパティは変更できません。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **管理者以外のユーザーがレプリケーション モニターを使用できるようにするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 管理者以外のユーザーがレプリケーションモニターを使用できるようにするには、 **sysadmin**固定サーバーロールのメンバーが、ディストリビューションデータベースにユーザーを追加し、そのユーザーをロールに割り当てる必要があり `replmonitor` ます。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>管理者以外のユーザーがレプリケーション モニターを使用できるようにするには  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、ディストリビューターに接続し、サーバー ノードを展開します。  
  
2.  **[データベース]**、 **[システム データベース]** の順に展開してから、ディストリビューション データベース (既定の名前は **distribution** ) を展開します。  
  
3.  **[セキュリティ]** を展開し、 **[ユーザー]** を右クリックしてから、 **[新しいユーザー]** をクリックします。  
  
4.  ユーザー名とユーザーのログインを入力します。  
  
5.  の既定のスキーマを選択し `replmonitor` ます。  
  
6.  [ `replmonitor` **データベースロールのメンバーシップ**] グリッドで、このチェックボックスをオンにします。  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>固定データベース ロール replmonitor にユーザーを追加するには  
  
1.  ディストリビューターのディストリビューション データベースで [sp_helpuser (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql) を実行します。 ユーザーが結果セットのに一覧表示されていない場合は、 `UserName` [CREATE User &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)ステートメントを使用して、ディストリビューションデータベースへのアクセス権をユーザーに付与する必要があります。  
  
2.  ディストリビューター側のディストリビューションデータベースに対して、パラメーターに値を指定して[sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)を実行し `replmonitor` **@rolename** ます。 ユーザーが結果セットのに一覧表示されている場合 `MemberName` 、そのユーザーは既にこのロールに属しています。  
  
3.  ユーザーがロールに属していない場合は `replmonitor` 、ディストリビューター側のディストリビューションデータベースに対して[Sp_addrolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)を実行します。 に値を、 `replmonitor` **@rolename** にを追加するデータベースユーザーまたは Windows ログインの名前を指定し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] **@membername** ます。  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>固定データベース ロール replmonitor からユーザーを削除するには  
  
1.  ユーザーがロールに属していることを確認するには `replmonitor` 、ディストリビューター側のディストリビューションデータベースに対して[Sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)を実行し、の値をに指定し `replmonitor` **@rolename** ます。 対象のユーザーが結果セットの `MemberName` に含まれていなかった場合、そのユーザーは現在、このロールに所属していません。  
  
2.  ユーザーがロールに属している場合は `replmonitor` 、ディストリビューター側のディストリビューションデータベースに対して[Sp_droprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)を実行します。 に値を、には `replmonitor` **@rolename** 削除するデータベースユーザーまたは Windows ログインの名前を指定し **@membername** ます。  
  
  
