---
title: "データベース スキーマの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.schemas.general.f1"
helpviewer_keywords: 
  - "Management Studio を使用したスキーマの作成"
  - "CREATE SCHEMA [Management Studio]"
  - "データベース スキーマ"
  - "作成するスキーマ [SQL Server]"
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# データベース スキーマの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **スキーマを作成する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   新しいスキーマは、データベース ユーザー、データベース ロール、またはアプリケーション ロールのいずれかのデータベース レベルのプリンシパルが所有します。 スキーマ内に作成されるオブジェクトはスキーマの所有者が所有し、**sys.objects** 内の **principal_id** は NULL になります。 スキーマが含まれるオブジェクトの所有権は、データベース レベルのプリンシパルに譲渡できますが、スキーマ内のオブジェクトに対する CONTROL 権限は常にスキーマ所有者が保持します。  
  
-   データベース オブジェクトを作成する場合に、有効なドメイン プリンシパル (ユーザーまたはグループ) をオブジェクト所有者として指定すると、ドメイン プリンシパルがスキーマとしてデータベースに追加されます。 新しいスキーマは、そのドメイン プリンシパルが所有します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
  
-   データベースに対する CREATE SCHEMA 権限が必要です。  
  
-   別のユーザーを、作成されるスキーマの所有者として指定する場合、呼び出し元は、そのユーザーに対する IMPERSONATE 権限を持っている必要があります。 データベース ロールを所有者として指定する場合、呼び出し元は、データベース ロールのメンバーシップまたはデータベース ロールに対する ALTER 権限のいずれかを持っている必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
##### スキーマを作成するには  
  
1.  オブジェクト エクスプローラーで、 **[データベース]** フォルダーを展開します。  
  
2.  新しいデータベース スキーマを作成するデータベースを展開します。  
  
3.  **[セキュリティ]** フォルダーを右クリックし、**[新規作成]** をポイントして、**[スキーマ]** をクリックします。  
  
4.  **[スキーマ - 新規作成]** ダイアログ ボックスの **[全般]** ページで、**[スキーマ名]** ボックスに新しいスキーマの名前を入力します。  
  
5.  **[スキーマの所有者]** ボックスに、スキーマを所有するデータベース ユーザーまたはロールの名前を入力します。 または、 **[検索]** をクリックして **[ロールとユーザーの検索]** ダイアログ ボックスを開きます。  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### 追加オプション  
 **[スキーマ – 新規作成]** ダイアログ ボックスには、 **[権限]** と **[拡張プロパティ]**という 2 つのページもあり、それぞれにオプションが用意されています。  
  
-   **[権限]** ページには、すべてのセキュリティ保護可能なリソースと、ログインに付与できる、セキュリティ保護可能なリソースに対する権限が一覧表示されます。  
  
-   **[拡張プロパティ]** ページでは、カスタム プロパティをデータベース ユーザーに追加できます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### スキーマを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 詳細については、「[CREATE SCHEMA &#40;Transact-SQL&#41;](../../../t-sql/statements/create-schema-transact-sql.md)」を参照してください。  
  
  