---
title: "スキーマ オプションの指定 | Microsoft Docs"
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
  - "スキーマ [SQL Server レプリケーション]、オプション"
  - "アーティクル [SQL Server レプリケーション]、トランザクション レプリケーション オプション"
  - "アーティクル [SQL Server レプリケーション]、マージ レプリケーション オプション"
  - "アーティクル [SQL Server レプリケーション]、スキーマ オプション"
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# スキーマ オプションの指定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマのオプションを指定する方法について説明します。 テーブルまたはビューをパブリッシュするとき、パブリッシュされたオブジェクト用にレプリケートされるオブジェクトの作成オプションを制御できます。 アーティクルが作成されるときにこれらのオプションを設定することができ、後で変更することもできます。 アーティクルに対してオプションを明示的に指定しなかった場合、既定のオプションが定義されます。  
  
> [!NOTE]  
>  レプリケーションのストアド プロシージャを使用した場合の既定のスキーマ オプションは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使ってアーティクルを追加するときの既定のオプションとは異なる場合があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
-   **スキーマ オプションを指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションの作成後にスキーマ オプションを変更する場合は、新しいスナップショットを生成する必要があります。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   スキーマ オプションの完全な一覧については、 **@schema_option** のパラメーター [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)  [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 制約およびトリガーをサブスクライバーにコピーするかどうかなどのスキーマ オプションを指定、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックス。 このタブはパブリケーションの新規作成ウィザードで表示され、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### スキーマ オプションを指定するには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、アーティクルを選択し、をクリックし、 **アーティクルのプロパティ**します。  
  
2.  スキーマ オプションの変更を適用するアーティクルを選択します。  
  
    -   をクリックして **設定のプロパティの強調表示されている \< ObjectType> 記事** を起動する、 **アーティクルのプロパティ - \< ObjectName>** ] ダイアログ ボックス。 プロパティのオブジェクト ペインで強調表示されているオブジェクトだけにこのダイアログ ボックスで行われた変更が適用される、 **記事** ページです。  
  
    -   をクリックして **プロパティをすべての設定 \< ObjectType> 記事** を起動する、 **すべてのプロパティ \< ObjectType> 記事** ] ダイアログ ボックス。 プロパティこのダイアログ ボックスで行った変更は、オブジェクト] ペインで、その種類のすべてのオブジェクトに適用されます、 **記事** ] ページで、パブリケーション用に選択されていないものなどです。  
  
        > [!NOTE]  
        >  行われたプロパティの変更、 **すべてプロパティ \< ObjectType> 記事** ダイアログ ボックスの上書きで以前に行われた、 **アーティクルのプロパティ - \< ObjectName>** ] ダイアログ ボックス。 たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。 次に、それぞれのオブジェクトに対してプロパティを設定します。  
  
3.   **オブジェクトをコピーし、サブスクライバーに設定** と **対象オブジェクト** のセクションでは、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックスで、オプションの値を指定します。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
5.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 16 進値であるスキーマのオプションが指定されている、 [|(ビット演算 OR)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) 1 つまたは複数のオプションの結果です。 詳細については、次を参照してください。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) と [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。  
  
> [!NOTE]  
>  ビットごとの演算を実行する際は、あらかじめ、スキーマ オプションの値を **binary** から **int** に変換しておく必要があります。 詳細については、次を参照してください。 [CAST および CONVERT & #40 です。Transact SQL と #41;](../../../t-sql/functions/cast-and-convert-transact-sql.md)します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを定義するときにスキーマ オプションを指定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, 、データベース オブジェクトの型 **@type**, 、および [|(ビット演算 OR)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) 結果の 1 つまたは複数のスキーマ オプションの **@schema_option**します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### マージ パブリケーションのアーティクルを定義するときにスキーマ オプションを指定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, 、および [|(ビット演算 OR)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) 結果の 1 つまたは複数のスキーマ オプションの **@schema_option**します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションの既存のアーティクルに設定されているスキーマ オプションを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)します。 **@publication** と **@article**に、それぞれアーティクルが属しているパブリケーションの名前およびアーティクル名を指定します。 値に注意してください、 **schema_option** 結果セット内の列です。  
  
2.  実行、 [& (ビット演算 AND)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) 操作手順 1 と目的のスキーマから値を使用してオプションのかどうか、オプションは設定を決定する値。  
  
    -   実行結果が **0**の場合、オプションは設定されていません。  
  
    -   実行結果がオプションの値の場合、そのオプションは既に設定されています。  
  
3.  オプションが設定されていない場合、実行、 [|(ビット演算 OR)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) 手順 1. の値と目的のスキーマ オプションの値を使用して操作します。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, のアーティクルの名前 **@article**, の値 **schema_option** の **@property**, 、手順 3 の 16 進数の結果と **@value**します。  
  
5.  スナップショット エージェントを実行して、新しいスナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
#### マージ パブリケーションの既存のアーティクルのスキーマ オプションを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)します。 **@publication** と **@article**に、それぞれアーティクルが属しているパブリケーションの名前およびアーティクル名を指定します。 値に注意してください、 **schema_option** 結果セット内の列です。  
  
2.  実行、 [& (ビット演算 AND)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) 操作手順 1 と目的のスキーマから値を使用してオプションのかどうか、オプションは設定を決定する値。  
  
    -   実行結果が **0**の場合、オプションは設定されていません。  
  
    -   実行結果がオプションの値の場合、そのオプションは既に設定されています。  
  
3.  オプションが設定されていない場合、実行、 [|(ビット演算 OR)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) 手順 1. の値と目的のスキーマ オプションの値を使用して操作します。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, のアーティクルの名前 **@article**, の値 **schema_option** の **@property**, 、手順 3 の 16 進数の結果と **@value**します。  
  
5.  スナップショット エージェントを実行して、新しいスナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
## 参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [トランザクション レプリケーションのアーティクル オプション](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
  