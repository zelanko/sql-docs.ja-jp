---
title: "[サブスクライバー] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subscribers.f1"
helpviewer_keywords: 
  - "サブスクライバー [SQL Server レプリケーション]"
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# [サブスクライバー]
  指定の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、選択したパブリケーションに対するサブスクリプションを受信するサブスクライバー。  
  
## オプション  
 **[サブスクライバー]**  
 グリッドを使用して、対応するチェック ボックスをオンに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で選択したパブリケーションに対するサブスクライバーとしてデータ ソース、 **パブリケーション** ページです。 サブスクライバーが一覧にない場合、 **[サブスクライバーの追加]** または **[SQL Server サブスクライバーの追加]**をクリックします。  
  
 **サブスクリプション データベース**  
 情報が表示され、このコラムで使用できるアクションに表示されているサブスクライバーの種類によって異なります。、 **サブスクライバー** 列。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合、 **[サブスクリプション データベース]** の一覧からサブスクリプション データベースを選択するか、同じ一覧から **[新しいデータベース]** コマンドを選択して新しいデータベースを作成します。  
  
    > [!NOTE]  
    >  パブリッシャーをサブスクライバーとして有効にする場合、サブスクリプション データベースはパブリケーション データベースとは別にする必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーの場合、サブスクリプション データベースは表示されません。 データベースおよびその他の接続情報を指定する、 **データ ソース名** のフィールド、 **非 SQL Server の追加** ] ダイアログ ボックス。 クリックして、このダイアログ ボックスは使用可能な **のサブスクライバーの追加** クリックし、 **非 SQL Server サブスクライバーの追加**します。  
  
 **[サブスクライバーの追加]**  
 サブスクライバーとして有効にできるサーバーの一覧に、サーバーを追加します。 このボタンは、次に示す条件がすべて満たされた場合に表示されます。  
  
-   選択したパブリケーションが、サブスクリプションの更新をサポートしないスナップショット パブリケーションまたはトランザクション パブリケーションである。  
  
    > [!NOTE]  
    >  サブスクライブしているパブリケーションに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクリプションが含まれており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーにまだ対応していない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクリプションを追加できません。  
  
-   サブスクリプションがプッシュ サブスクリプションである。  
  
-   選択したパブリケーションのパブリッシャーが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンである。  
  
 クリックすると **のサブスクライバーの追加** 2 つの選択肢のメニューを示しています: **[SQL Server サブスクライバー** と **非 SQL Server サブスクライバーの追加**します。 クリックして **非 SQL Server サブスクライバーの追加** Oracle または IBM DB2 サブスクライバーを追加します。  
  
 **[SQL Server サブスクライバーの追加]**  
 サブスクライバーとして有効にできるサーバーの一覧に、サーバーを追加します。 このボタンは、次のいずれかの条件が満たされた場合に表示されます。  
  
-   選択したパブリケーションが、サブスクリプションの更新をサポートするマージ パブリケーション、スナップショット パブリケーション、またはトランザクション パブリケーションである。  
  
-   サブスクリプションがプル サブスクリプションである。  
  
-   選択したパブリケーションのパブリッシャーが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]よりも古いバージョンである。 古いバージョンの場合、このボタンは次の条件のいずれかが満たされた場合にのみ表示されます。  
  
    -   パブリッシャーの **sysadmin** 固定サーバー ロールのメンバーである。  
  
    -   サブスクライバーが、 **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[サブスクライバー]** ページに追加されている。  
  
    -   パブリケーションで匿名サブスクリプションが許可されている。  
  
## 参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  