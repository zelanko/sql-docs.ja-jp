---
title: "Oracle パブリッシャーのデータ型マッピングの指定 | Microsoft Docs"
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
  - "Oracle パブリッシング [SQL Server レプリケーション]、データ型マッピング"
  - "データ型 [SQL Server レプリケーション]、Oracle パブリッシング"
  - "マッピング データ型 [SQL Server レプリケーション]"
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Oracle パブリッシャーのデータ型マッピングの指定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、Oracle パブリッシャーのデータ型マッピングを指定する方法について説明します。 Oracle パブリッシャーには一連の既定のデータ型マッピングが用意されていますが、パブリケーションによっては、こうした既定のマッピングとは異なるマッピングの指定が必要になる場合もあります。  
  
 **このトピックの内容**  
  
-   **Oracle パブリッシャーのデータ型マッピングを指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 上のデータ型のマッピングの指定、 **データ マッピング** のタブ、 **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックス。 これは、 **記事** パブリケーションの新規作成ウィザードのページと **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [Oracle データベースからパブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### データ型マッピングを指定するには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、テーブルを選択し、をクリックして **アーティクルのプロパティ**します。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **データ マッピング** のタブ、 **アーティクルのプロパティ - \< 記事>** からマッピングを選択] ダイアログ ボックス、 **サブスクライバーのデータ型** 列。  
  
    -   データ型によっては、可能なマッピングが 1 つしかない場合があります。このような場合、プロパティ グリッドの列は読み取り専用になります。  
  
    -   データ型によっては、複数のデータ型を選択できる場合があります。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] では、アプリケーションに別のマッピングが必要でない限り、既定のマッピングを使うことをお勧めします。 詳しくは、「 [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)」をご覧ください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーションのストアド プロシージャを使用すると、カスタム データ型マッピングをプログラムから指定できます。 データ型をマップ間ときに使用される既定のマッピングを設定することもできます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース管理システム (DBMS)。 詳しくは、「 [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)」をご覧ください。  
  
#### Oracle パブリケーションのアーティクル作成時にカスタム データ型マッピングを定義するには  
  
1.  Oracle パブリケーションが存在しない場合は、Oracle パブリケーションを作成します。  
  
2.  ディストリビューターで実行 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 値を指定して **0** の **@use_default_datatypes**します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
3.  ディストリビューターで実行 [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) パブリッシュされたアーティクルで列の既存のマッピングを表示します。  
  
4.  ディストリビューターで実行 [sp_changearticlecolumndatatype](../../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md)します。 **@publisher**に Oracle パブリッシャーの名前を指定し、 **@publication**、 **@article**、および **@column** を指定して、パブリッシュする列を定義します。 マップする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型名を **@type**に指定し、該当する **@length**、 **@precision**、および **@scale**を指定します。  
  
5.  ディストリビューターで実行 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。 これにより、Oracle パブリケーションからスナップショットを生成するときに使用するビューが作成されます。  
  
#### データ型に対する既定のマッピングを指定するには  
  
1.  (省略可能)ディストリビューターのデータベースで、次のように実行します。 [sp_getdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)します。 指定 **@source_dbms**, 、**@source_type**, 、**@destination_dbms**, 、**@destination_version**, 、マップ元 DBMS を識別するために必要なその他のパラメーターです。 マップ先 DBMS で現在マップされているデータ型の情報は、出力パラメーターを使って返されます。  
  
2.  (省略可能)ディストリビューターのデータベースで、次のように実行します。 [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)します。 指定 **@source_dbms** を結果セットをフィルター処理するために必要なその他のパラメーターとします。 値に注意してください **mapping_id** 結果に目的のマッピングを設定します。  
  
3.  ディストリビューターのデータベースで、次のように実行します。 [sp_setdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)します。  
  
    -   目的の値がわかっている場合 **mapping_id** の指定手順 2. で取得した **@mapping_id**します。  
  
    -   不明な場合、 **mapping_id**, 、パラメーターを指定 **@source_dbms**, 、**@source_type**, 、**@destination_dbms**, 、**@destination_type**, 、既存のマッピングを識別するために必要なその他のパラメーターです。  
  
#### 特定の Oracle データ型に対して有効なデータ型を見つけるには  
  
1.  ディストリビューターのデータベースで、次のように実行します。 [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)します。 値を指定して **ORACLE** の **@source_dbms** を結果セットをフィルター処理するために必要なその他のパラメーターとします。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では数値の Oracle データ型の列にマップされているので [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型 **数値**(38, 38)、既定のデータ型ではなく **float**します。  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_1.sql)]  
  
 次のクエリの例では、Oracle 9 データ型の **CHAR**について、既定のマッピングと代替マッピングを返します。  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_2.sql)]  
  
 次のクエリの例では、Oracle 9 データ型の **NUMBER** で、小数点以下桁数または有効桁数を指定しなかった場合に使用される既定のマッピングを返します。  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_3.sql)]  
  
## 参照  
 [Oracle パブリッシャーのデータ型マッピング](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [異種データベース レプリケーション](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)  
  
  