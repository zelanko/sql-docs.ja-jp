---
title: "管理者以外のユーザーがレプリケーション モニターを使用できるようにする | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レプリケーション モニター, 管理者以外のアクセス"
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# 管理者以外のユーザーがレプリケーション モニターを使用できるようにする
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、管理者以外のユーザーがレプリケーション モニターを使用できるようにする方法について説明します。 レプリケーション モニターは、次のロールのメンバーになっているユーザーが使用できます。  
  
-   **sysadmin** 固定サーバー ロール  
  
     これらのユーザーはレプリケーションを監視することができ、また、エージェント スケジュール、エージェント プロファイルなどのレプリケーション プロパティの変更に対するフル コントロール権限を持っています。  
  
-   ディストリビューション データベースの **replmonitor** データベース ロール  
  
     これらのユーザーはレプリケーションを監視できますが、レプリケーション プロパティは変更できません。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **管理者以外のユーザーがレプリケーション モニターを使用できるようにするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 非管理者によるレプリケーション モニターでのメンバーの使用を許可するように、 **sysadmin** 固定サーバー ロールがディストリビューション データベースにユーザーを追加し、そのユーザーを割り当てる必要があります、 **replmonitor** ロールです。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### 管理者以外のユーザーがレプリケーション モニターを使用できるようにするには  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、ディストリビューターに接続し、サーバー ノードを展開します。  
  
2.  展開 **データベース**, 、展開 **システム データベース**, 、ディストリビューション データベースを展開し、(という名前 **配布** 既定では)。  
  
3.  展開 **セキュリティ**, を右クリックして **ユーザー**, 、クリックして **新しいユーザー**します。  
  
4.  ユーザー名とユーザーのログインを入力します。  
  
5.  既定のスキーマ **[replmonitor]**を選択します。  
  
6.  **[データベース ロールのメンバーシップ]** の **[replmonitor]** チェック ボックスをオンにします。  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 固定データベース ロール replmonitor にユーザーを追加するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_helpuser & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)します。 ユーザーが表示されない場合 **ユーザー名** 結果セットに、ユーザー必要がありますへのアクセス許可を使って、ディストリビューション データベース、 [ユーザーの作成と #40 です。Transact SQL と #41;](../../../t-sql/statements/create-user-transact-sql.md) ステートメント。  
  
2.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_helprolemember & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md), の値を指定する **replmonitor** の **@rolename** パラメーター。 対象のユーザーが結果セットの **MemberName** に含まれていた場合、そのユーザーは既にこのロールに所属しています。  
  
3.  ユーザーが属していない場合、 **replmonitor** ロール、実行 [sp_addrolemember & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) ディストリビューター側でディストリビューション データベースです。 **@rolename** には値 **replmonitor** を、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] @membername **には、追加するデータベース ユーザーの名前または**Windows ログイン名を指定します。  
  
#### 固定データベース ロール replmonitor からユーザーを削除するには  
  
1.  ユーザーが所属することを確認する、 **replmonitor** ロール、実行 [sp_helprolemember (& a) #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) ディストリビューターのディストリビューション データベースでの値を指定して **replmonitor** の **@rolename**します。 対象のユーザーが結果セットの **MemberName** に含まれていなかった場合、そのユーザーは現在、このロールに所属していません。  
  
2.  ユーザーが属している場合、 **replmonitor** ロール、実行 [sp_droprolemember & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) ディストリビューター側でディストリビューション データベースです。 **@rolename** には値 **replmonitor** を、 **@membername**には、削除するデータベース ユーザーの名前または Windows ログイン名を指定します。  
  
  