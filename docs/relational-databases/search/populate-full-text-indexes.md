---
title: "フルテキスト インデックスの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インデックスの作成 [フルテキスト検索]"
  - "増分作成 [フルテキスト検索]"
  - "作成 [フルテキスト検索]"
  - "フルテキスト検索 [SQL Server], 作成"
  - "クロール [フルテキスト検索]"
  - "フルテキスト インデックス自動更新"
  - "変更の追跡に基づく作成 [フルテキスト検索]"
  - "手動更新 [フルテキスト検索]"
  - "手動作成 [フルテキスト検索]"
  - "自動作成 [フルテキスト検索]"
  - "キー列のフルテキスト インデックス [SQL Server]"
  - "完全作成 [フルテキスト検索]"
  - "フルテキスト インデックス [SQL Server], 作成"
ms.assetid: 76767b20-ef55-49ce-8dc4-e77cb8ff618a
caps.latest.revision: 78
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 75
---
# フルテキスト インデックスの作成
  フルテキスト インデックスの作成と保持では、*作成* (または *クロール*) と呼ばれるプロセスを使用してインデックスが作成されます。  
  
##  <a name="types"></a> 作成の種類  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポートされている作成には、完全作成、変更の追跡に基づく自動作成または手動作成、およびタイムスタンプに基づく増分作成があります。  
  
### すべてのカタログの作成  
 すべてのカタログの作成では、テーブルまたはインデックス付きビューのすべての行に対してインデックス エントリが作成されます。 フルテキスト インデックスのすべてのカタログの作成では、ベース テーブルまたはインデックス付きビューのすべての行に対してインデックス エントリが作成されます。  
  
 既定では、新しいフルテキスト インデックスが作成されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってすぐにそのカタログが作成されます。 ただし、すべてのカタログの作成では大量のリソースが消費される可能性があります。 このため、ピーク期間にフルテキスト インデックスを作成する場合は、すべてのカタログの作成をオフピーク時間まで遅らせることが推奨されています (特にフルテキスト インデックスのベース テーブルが大きい場合)。 ただし、インデックスが属するフルテキスト カタログは、そのすべてのフルテキスト インデックスのカタログが作成されるまで使用できません。 フルテキスト インデックスを作成する際に直ちにカタログを作成しない場合は、CREATE FULLTEXT INDEX ステートメントで CHANGE_TRACKING OFF および NO POPULATION 句を指定します。 CHANGE_TRACKING MANUAL を指定すると、Full-Text Engine はステートメントを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] START FULL POPULATION 句または START INCREMENTAL POPULATION 句を指定して ALTER FULLTEXT INDEX ステートメントを実行するまで、新しいフルテキスト インデックスを作成しません。 詳細については、このトピックの後半の例「A.  完全作成を実行せずにフルテキスト インデックスを作成する」および「B.  テーブルで完全作成を実行する」を参照してください。  
  
 [先頭に戻る](#top)  
  
### 変更の追跡に基づくカタログ作成  
 必要に応じて、変更の追跡を使用して、完全作成が最初に実行された後のフルテキスト インデックスを保持することができます。 変更の追跡には若干のオーバーヘッドが伴います。これは、前回のカタログ作成以降にベース テーブルに対して行われた変更を追跡するテーブルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で保持されるためです。 変更の追跡を使用すると、ベース テーブルまたはインデックス付きビューで更新、削除、または挿入によって変更された行の記録が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で保持されます。 WRITETEXT および UPDATETEXT によるデータの変更は、フルテキスト インデックスには反映されず、変更の監視でも取得されません。  
  
> [!NOTE]  
>  **timestamp** 列を含んでいるテーブルには、増分作成を使用できます。  
  
 インデックス作成時に変更の追跡を有効にすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で新しいフルテキスト インデックスが作成された直後にそのインデックスですべてのカタログの作成が実行されます。 それ以降は、変更が追跡されてフルテキスト インデックスに反映されます。 変更の追跡には、自動 (CHANGE_TRACKING AUTO オプション) と手動 (CHANGE_TRACKING MANUAL オプション) の 2 種類があります。 既定では自動で変更が追跡されます。  
  
 変更の追跡の種類によって、フルテキスト インデックスのカタログ作成方法が次のように決まります。  
  
-   自動でのカタログ作成  
  
     既定では、または CHANGE_TRACKING AUTO を指定すると、Full-Text Engine によってフルテキスト インデックスに自動的にカタログが作成されます。 すべてのカタログの作成が最初に実行された後に、ベース テーブルでデータが変更されると変更が追跡され、追跡された変更が自動的に反映されます。 ただし、フルテキスト インデックスはバックグラウンドで更新されるため、変更が直ちにインデックスに反映されないこともあります。  
  
     **自動でのカタログ作成を指定して変更の追跡を設定するには**  
  
    -   [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md) … WITH CHANGE_TRACKING AUTO  
  
    -   [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) … SET CHANGE_TRACKING AUTO  
  
     詳細については、このトピックの後半の例「E.  自動で変更が追跡されるようにフルテキスト インデックスを変更する」を参照してください。  
  
-   手動でのカタログ作成  
  
     CHANGE_TRACKING MANUAL を指定すると、Full-Text Engine ではフルテキスト インデックスに対して手動作成が使用されます。 完全作成が最初に実行された後に、ベース テーブルでデータが変更されると変更が追跡されます。 ただしその変更は、ALTER FULLTEXT INDEX ... START UPDATE POPULATION ステートメントを実行するまで反映されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用すると、この [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを定期的に呼び出すことができます。  
  
     **手動でのカタログ作成を指定して変更の追跡を開始するには**  
  
    -   [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md) … WITH CHANGE_TRACKING MANUAL  
  
    -   [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) … SET CHANGE_TRACKING MANUAL  
  
     詳細については、このトピックの後半の例「C.  手動で変更を追跡するようにフルテキスト インデックスを作成する」および「D.  手動でのカタログ作成を実行する」を参照してください。  
  
 **変更の追跡を無効にするには**  
  
-   [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md) … WITH CHANGE_TRACKING OFF  
  
-   [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) … SET CHANGE_TRACKING OFF  
  
 [先頭に戻る](#top)  
  
### タイムスタンプに基づく増分作成  
 増分作成は、フルテキスト インデックスに手動でカタログを作成するためのもう 1 つのメカニズムです。 増分作成は、CHANGE_TRACKING が MANUAL または OFF に設定されているフルテキスト インデックスに対して実行できます。 フルテキスト インデックスの最初のカタログ作成が増分作成の場合、すべての行にインデックスが付けられるため、完全作成と同じになります。  
  
 増分作成では、インデックスが設定されたテーブルに **timestamp** データ型の列が存在する必要があります。 **timestamp** 型の列が存在しない場合には、増分作成を実行できません。 **timestamp** 型の列を含んでいないテーブルで増分作成を要求すると、完全作成が実行されます。 また、前回のカタログ作成後にテーブルのフルテキスト インデックスに影響するようなメタデータの変更があった場合、増分作成の要求はすべてのカタログの作成として実行されます。 これには、列、インデックス、またはフルテキスト インデックスの定義を変更したことによるメタデータの変更が含まれます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** 列を使用して前回の作成後に変更された行が識別されます。 増分作成では、前回のカタログ作成後、または作成中に追加、削除、または変更された行のフルテキスト インデックスが更新されます。 テーブルで大量の挿入が行われた場合は、手動でのカタログ作成よりも増分作成を使用した方が効率的です。  
  
 作成が終わると、Full-Text Engine は新しい **timestamp** 型の値を記録します。 この値は、SQL Gatherer が検出した **timestamp** 型の最大値です。 今後、増分作成を開始するときには、この値が使用されます。  
  
 増分作成を実行するには、START INCREMENTAL POPULATION 句を指定して ALTER FULLTEXT INDEX ステートメントを実行します。  
  
 [先頭に戻る](#top)  
  
##  <a name="examples"></a> フルテキスト インデックスの作成の例  
  
> [!NOTE]  
>  このセクションの例では、`Production.Document` サンプル データベースの `HumanResources.JobCandidate` テーブルまたは `AdventureWorks` テーブルを使用します。  
  
### A. 完全作成を実行せずにフルテキスト インデックスを作成する  
 次の例では、`Production.Document` サンプル データベースの `AdventureWorks` テーブルにフルテキスト インデックスを作成します。 この例では、WITH CHANGE_TRACKING OFF, NO POPULATION を使用して、最初の完全作成を遅らせます。  
  
```  
CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
CREATE FULLTEXT CATALOG AW_Production_FTCat;  
CREATE FULLTEXT INDEX ON Production.Document  
(  
    Document                         --Full-text index column name   
        TYPE COLUMN FileExtension    --Name of column that contains file type information  
        Language 1033                 --1033 is LCID for the English language  
)  
    KEY INDEX ui_ukDoc  
    ON AW_Production_FTCat  
    WITH CHANGE_TRACKING OFF, NO POPULATION;  
GO  
  
```  
  
### B. テーブルで完全作成を実行する  
 次の例では、`Production.Document` サンプル データベースの `AdventureWorks` テーブルで完全作成を実行します。  
  
```  
ALTER FULLTEXT INDEX ON Production.Document  
   START FULL POPULATION;  
```  
  
### C. 手動での変更の追跡によってフルテキスト インデックスを作成する  
 次の例では、`HumanResources.JobCandidate` サンプル データベースの `AdventureWorks` テーブルで、手動でのカタログ作成を指定した変更の追跡を使用するフルテキスト インデックスを作成します。  
  
```  
USE AdventureWorks;  
GO  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH CHANGE_TRACKING=MANUAL;  
GO  
```  
  
### D. 手動作成を実行する  
 次の例では、`HumanResources.JobCandidate` サンプル データベースの `AdventureWorks` テーブルで、変更が追跡されるフルテキスト インデックスに対して手動でのカタログ作成を実行します。  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate START UPDATE POPULATION;  
GO  
```  
  
### E. 自動の変更の追跡を使用するようにフルテキスト インデックスを変更する  
 次の例では、`HumanResources.JobCandidate` サンプル データベースの `AdventureWorks` テーブルで、自動作成に変更の追跡を使用するようにフルテキスト インデックスを変更します。  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate SET CHANGE_TRACKING AUTO;  
GO   
```  
  
 [先頭に戻る](#top)  
  
##  <a name="create"></a> 増分作成のスケジュールの作成または変更  
  
#### Management Studio で増分作成のスケジュールを作成または変更するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開します。  
  
2.  **[データベース]** を展開し、フルテキスト インデックスを含むデータベースを展開します。  
  
3.  **[テーブル]** を展開します。  
  
 フルテキスト インデックスが定義されているテーブルを右クリックし、**[フルテキスト インデックス]** コンテキスト メニューの **[フルテキスト インデックス]** をクリックして、**[プロパティ]** をクリックします。 **[フルテキスト インデックスのプロパティ]** ダイアログ ボックスが表示されます。  
  
1.  **[ページの選択]** ペインで [スケジュール] をクリックします。  
  
     このページでは、フルテキスト インデックスのベース テーブルまたはインデックス付きビューの増分作成を開始する SQL Server エージェント ジョブのスケジュールを作成または管理できます。  
  
    > [!IMPORTANT]  
    >  ベース テーブルまたはビューに **timestamp** データ型の列が含まれていない場合は、完全作成が実行されます。  
  
     次のオプションがあります。  
  
    -   新しいスケジュールを作成するには、**[新規作成]** をクリックします。  
  
         スケジュールを作成できる **[新しいフルテキスト インデックス テーブルのスケジュール]** ダイアログ ボックスが表示されます。 スケジュールを保存するには、**[OK]** をクリックします。  
  
        > [!IMPORTANT]  
        >  **[フルテキスト インデックスのプロパティ]** ダイアログ ボックスを閉じると、新しいスケジュールが SQL Server エージェント ジョブ (*database_name*.*table_name* でテーブルの増分作成を開始) に関連付けられます。 フルテキスト インデックスのスケジュールを複数作成した場合は、すべてのスケジュールで同じジョブが使用されます。  
  
    -   スケジュールを変更するには、スケジュールを選択して **[編集]** をクリックします。  
  
         スケジュールを変更できる **[新しいフルテキスト インデックス テーブルのスケジュール]** ダイアログ ボックスが表示されます。  
  
        > [!NOTE]  
        >  ジョブの変更については、「[ジョブの変更](../../ssms/agent/modify-a-job.md)」を参照してください。  
  
    -   スケジュールを削除するには、スケジュールを選択して **[削除]** をクリックします。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 [先頭に戻る](#top)  
  
##  <a name="crawl"></a> フルテキスト作成 (クロール) で発生したエラーのトラブルシューティング  
 クロール時にエラーが発生すると、フルテキスト検索クロール ログ記録機能によってクロール ログが作成および保持されます。このログはプレーンテキスト ファイルです。 各クロール ログは特定のフルテキスト カタログに対応します。 既定では、特定のインスタンス (この場合は最初のインスタンス) のクロール ログは %ProgramFiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\LOG フォルダーにあります。 クロール ログは次のような規則に従って命名されます。  
  
 SQLFT\<DatabaseID>\<FullTextCatalogID>.LOG[\<n>]  
  
 \<**DatabaseID**>  
 データベースの ID です。 \<**dbid**> は、ゼロで始まる 5 桁の数字です。  
  
 \<**FullTextCatalogID**>  
 フルテキスト カタログ ID です。 \<**catid**> は、ゼロで始まる 5 桁の数字です。  
  
 \<**n**>  
 同じフルテキスト カタログに 1 つ以上のクロール ログが存在することを示す整数です。  
  
 たとえば、SQLFT0000500008.2 はデータベース ID が 5 で、フルテキスト カタログ ID が 8 のクロール ログ ファイルです。 ファイル名の最後の 2 は、このデータベースとカタログのペアに 2 つのクロール ログ ファイルが存在することを示しています。  
  
 [先頭に戻る](#top)  
  
## 参照  
 [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)   
 [フルテキスト検索の概要](../../relational-databases/search/get-started-with-full-text-search.md)   
 [フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
  