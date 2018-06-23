---
title: 管理者以外のユーザーがレプリケーション モニターを使用できるようにする | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: 36
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f8b98f90d41174bb2a58cd1bf96b8b4f08e83f38
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072977"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>管理者以外のユーザーがレプリケーション モニターを使用できるようにする
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、管理者以外のユーザーがレプリケーション モニターを使用できるようにする方法について説明します。 レプリケーション モニターは、次のロールのメンバーになっているユーザーが使用できます。  
  
-   **sysadmin** 固定サーバー ロール  
  
     これらのユーザーはレプリケーションを監視することができ、また、エージェント スケジュール、エージェント プロファイルなどのレプリケーション プロパティの変更に対するフル コントロール権限を持っています。  
  
-   `replmonitor`ディストリビューション データベース内のデータベース ロール。  
  
     これらのユーザーはレプリケーションを監視できますが、レプリケーション プロパティは変更できません。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **管理者以外のユーザーがレプリケーション モニターを使用できるようにするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 管理者以外のユーザーがレプリケーション モニター, のメンバーを使用できるように、 **sysadmin**固定サーバー ロールが、ディストリビューション データベースにユーザーを追加し、そのユーザーを割り当てる必要があります、`replmonitor`ロール。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>管理者以外のユーザーがレプリケーション モニターを使用できるようにするには  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、ディストリビューターに接続し、サーバー ノードを展開します。  
  
2.  **[データベース]**、 **[システム データベース]** の順に展開してから、ディストリビューション データベース (既定の名前は **distribution** ) を展開します。  
  
3.  **[セキュリティ]** を展開し、 **[ユーザー]** を右クリックしてから、 **[新しいユーザー]** をクリックします。  
  
4.  ユーザー名とユーザーのログインを入力します。  
  
5.  既定のスキーマを選択して`replmonitor`です。  
  
6.  選択、 `replmonitor`  チェック ボックス、**データベース ロールのメンバーシップ**グリッドです。  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>固定データベース ロール replmonitor にユーザーを追加するには  
  
1.  ディストリビューターのディストリビューション データベースで [sp_helpuser (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql) を実行します。 ユーザーが表示されない場合`UserName`結果セットに、ユーザー与える必要がありますを使って、ディストリビューション データベースへのアクセス、 [CREATE USER &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-user-transact-sql)ステートメントです。  
  
2.  ディストリビューターのディストリビューション データベースで、次のように実行します。 [sp_helprolemember &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)、の値を指定する`replmonitor`の、 **@rolename**パラメーター。 ユーザーが表示されている場合`MemberName`結果セットに、ユーザー既にこのロールに所属します。  
  
3.  ユーザーに属していない場合、`replmonitor`ロール、実行[sp_addrolemember &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)ディストリビューターのディストリビューション データベースでします。 値を指定して`replmonitor`の**@rolename**とデータベース ユーザーの名前または[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Windows ログイン用に追加された **@membername**です。  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>固定データベース ロール replmonitor からユーザーを削除するには  
  
1.  ユーザーに属していることを確認する、`replmonitor`ロール、実行[sp_helprolemember &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)ディストリビューターのディストリビューション データベースでの値を指定して`replmonitor`の**@rolename**. 対象のユーザーが結果セットの `MemberName` に含まれていなかった場合、そのユーザーは現在、このロールに所属していません。  
  
2.  ユーザーが属している場合、`replmonitor`ロール、実行[sp_droprolemember の各&#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)ディストリビューターのディストリビューション データベースでします。 値を指定して`replmonitor`の**@rolename**の名前と、データベース ユーザーまたは Windows ログインが削除されている **@membername**です。  
  
  
