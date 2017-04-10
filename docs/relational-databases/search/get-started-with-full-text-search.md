---
title: "フルテキスト検索の概要 | Microsoft Docs"
ms.date: "08/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "作成のフルテキスト カタログ [SQL Server]"
  - "作成するフルテキスト インデックス [SQL Server]"
  - "フルテキスト検索 [SQL Server], 説明"
  - "フルテキスト検索 [SQL Server], セットアップ"
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
caps.latest.revision: 76
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 72
---
# フルテキスト検索の概要
フルテキスト検索では、ワード ブレーカー、ステマー、ストップワード (ノイズ ワードとも呼ばれます) を含んだストップリスト、類義語辞典ファイルの各*言語コンポーネント*を使用して、複数の言語がサポートされます。 類義語辞典ファイルと (場合によって) ストップリストは、データベース管理者が構成する必要があります。 特定の類義語辞典ファイルは、対応する言語を使用するすべてのフルテキスト インデックスをサポートし、特定のストップリストには任意の数のフルテキスト インデックスを関連付けることができます。  
 
SQL Server データベースは既定でフルテキスト検索が有効ですが、最初に[フルテキスト カタログを作成](https://msdn.microsoft.com/library/bb326035.aspx)し、検索するテーブルまたはインデックス付きビューにフルテキスト インデックスを作成する必要があります。
 
 ## 手順 
 
 作成手順については、「[フルテキスト インデックス作成ウィザードの使用](https://msdn.microsoft.com/library/ms180091.aspx)」をご覧ください。

このトピックでは、考慮事項、例、および他のトピックへのリンクが示されています。
##  <a name="configure"></a> セットアップを計画する

フルテキスト検索用にデータベースのテーブルの列を構成するには、2 つの基本的な手順があります。  
  
- フルテキスト カタログを作成します。  
  
- 検索するテーブルまたはインデックス付きビューにフルテキスト インデックスを作成します。 

     フルテキスト インデックスは、Full-Text Engine により構築および管理されるトークンベースの特殊な機能インデックスです。 テーブルまたはビューにフルテキスト検索を作成するには、そのテーブルまたはビューに、単一列で非 NULL 値の一意なインデックスが作成されている必要があります。 Full-Text Engine では、テーブルの各行を一意の圧縮可能なキーにマップするために、この一意のインデックスが必要になります。 フルテキスト インデックスには、**char**、**varchar**、**nchar**、**nvarchar**、**text**、**ntext**、**image**、**xml**、**varbinary**、および **varbinary(max)** 列を含めることができます。 詳細については、「[フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)」をご覧ください。   
  
     各フルテキスト インデックスは、フルテキスト カタログに属している必要があります。 フルテキスト インデックスごとにテキスト カタログを作成するか、複数のフルテキスト インデックスを特定のカタログに関連付けることができます。 フルテキスト カタログは仮想オブジェクトであり、ファイル グループには属しません。 カタログは、フルテキスト インデックスのグループを指す論理的概念です。  
  

 フルテキスト インデックスと標準の SQL Server インデックスの違い:  
  
|フルテキスト インデックス|標準の SQL Server インデックス|  
|------------------------|--------------------------------|  
|1 つのテーブルに対し、1 つのフルテキスト インデックスしか使用できません。|1 つのテーブルに対し、複数の標準インデックスを使用できます。|  
|フルテキスト インデックスへのデータの追加は*作成*と呼ばれ、スケジュールによる要求または個別の要求のどちらかを通じて要求できます。または、新規データの追加と共に自動的に行うことができます。|関連するデータが挿入、更新、または削除されたときに、自動的に更新されます。|  
|同じデータベース内で 1 つ以上のフルテキスト カタログにグループ化されます。|グループ化されません。|  
    
##  <a name="options"></a> オプション  
  
### 列の言語  
 列の言語の選択については、「[フルテキスト インデックス作成時の言語の選択](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)」をご覧ください。  
  
### フルテキスト インデックスのファイル グループを選択する  
 フルテキスト インデックスの作成処理では、I/O が非常に集中します (高い頻度で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを読み取り、フィルター選択されたデータをフルテキスト インデックスに反映するため)。 I/O パフォーマンスの最大化に最適なデータベース ファイル グループにフルテキスト インデックスを配置するか、他のボリュームの別のファイル グループにフルテキスト インデックスを配置することをお勧めします。  
  
 テーブルのデータと、すべての関連フルテキスト カタログを、同じファイル グループに保存することをお勧めします。 パフォーマンス上の理由から、別々のボリュームに格納されている別々のファイル グループにテーブル データとフルテキスト インデックスを配置して、I/O 並列処理を最大限に高めることが必要になる場合もあります。  

  
### フルテキスト インデックスを割り当てる   
 
 変更が少ないテーブル、変更が多いテーブル、または特定の時間帯に頻繁に変更されるテーブルなど、同じ更新特性を持つテーブルは、同じフルテキスト カタログの下にまとめて関連付けることをお勧めします。 フルテキスト カタログの作成スケジュールをセットアップすると、データベースの利用率が高いときでもデータベース サーバーのリソース使用に大きな影響を及ぼすことなく、フルテキスト インデックスとテーブルの同期が維持されるようになります。  
  
 次のガイドラインを考慮してください。  
  
-   常に、一意なフルテキスト キーに利用可能な最小の一意なインデックスを選択してください。 4 バイトで、整数ベースのインデックスが最適です。これにより、ファイル システム内の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search サービスで必要となるリソースが大幅に減少します。 主キーが大きい場合 (100 バイト以上)、テーブル内の他の一意なインデックスを選択するか、または他の一意なインデックスを作成して、フルテキスト インデックス用のキーにすることを検討してください。 そうしないと、一意なフルテキスト キーのサイズが最大サイズ (900 バイト) を超えた場合、フルテキストの作成を続行できなくなります。  
  
-   数百万の行を持つテーブルにインデックスを作成する場合は、そのテーブル専用のフルテキスト カタログを割り当ててください。  
  
-   フルテキスト インデックスを作成するテーブル内の変更量だけではなく、そのテーブル内の行の総数についても考慮してください。 変更される行と、最後にフルテキスト インデックスを作成したときにテーブル内に存在した行の総数が数百万行に及ぶ場合は、そのテーブルを専用のフルテキスト カタログに割り当ててください。  

  
### ストップリストを関連付ける   
  *ストップリスト*は、ストップワード (ノイズ ワードとも呼ばれます) の一覧です。 ストップリストは各フルテキスト インデックスに関連付けられ、そのストップリスト内の単語がそのインデックスのフルテキスト クエリに適用されます。 既定では、システム ストップリストは、新しいフルテキスト インデックスに関連付けられます。 独自のストップリストを作成して使用することもできます。 詳細については、「[フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。  
  
 たとえば、次の [CREATE FULLTEXT STOPLIST](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、システム ストップリストからコピーして、myStoplist3 という名前の新しいフルテキスト ストップリストを作成します。  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 次の [ALTER FULLTEXT STOPLIST](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、myStoplist という名前のストップリストを変更して、単語 'en' をまずスペイン語用に、次にフランス語用に追加します。  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
    
## インデックスを更新する  
 標準の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インデックスと同様に、フルテキスト インデックスは、関連付けられたテーブルの中でデータが変更されると、自動的に更新されます。 これは既定の動作です。 指定したスケジュール間隔または手動でフルテキスト インデックスを最新の状態に保つこともできます。 フルテキスト インデックスの作成は時間とリソースの消費が大きいため、インデックスの更新は、通常、非同期プロセスで実行します。この非同期プロセスは、バックグラウンドで実行され、ベース テーブルの変更後にフルテキスト インデックスを最新の状態に維持します。 
 
 ベース テーブルのそれぞれの変更後すぐにフルテキスト インデックスを更新すると、リソースを大量に消費することがあります。 そのため、更新、挿入、または削除の率が非常に高い場合は、クエリのパフォーマンスが低下する可能性があります。 この問題が発生した場合、リソースについてクエリと競合しないよう、手動による変更追跡の更新をスケジュール設定して、適宜、大量の変更に対応することを検討してください。  
  
 FULLTEXTCATALOGPROPERTY 関数または OBJECTPROPERTYEX 関数を使用して、作成状態を監視します。 カタログ作成状態を取得するには、次のステートメントを実行します。  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 通常、カタログ全体の作成を実行している間は、結果として 1 が返されます。  
 

##  <a name="example"></a> 例: フルテキスト検索をセットアップする  
 次の 2 部構成の例では、AdventureWorks データベースに `AdvWksDocFTCat` という名前のフルテキスト カタログを作成し、次に、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] の `Document` テーブルにフルテキスト インデックスを作成します。 このステートメントによって、セットアップ時に指定した既定のディレクトリ内にフルテキスト カタログが作成されます。 `AdvWksDocFTCat` というフォルダーが既定のディレクトリ内にあります。  
  
1.  `AdvWksDocFTCat` という名前のフルテキスト カタログを作成するために、この例では、[CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md) ステートメントを使用します。  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  Document テーブルにフルテキスト インデックスを作成する前に、テーブルに一意の単一列で NULL 値にならないインデックスが含まれていることを確認します。 次の [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) ステートメントでは、Document テーブルの DocumentID 列に、一意のインデックス `ui_ukDoc` を作成します。  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  一意のキーを作成したら、次の [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md) ステートメントを使用して、`Document` テーブルにフルテキスト インデックスを作成できます。  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     この例で定義する TYPE COLUMN では、"Document" 列 (バイナリ型) の各行のドキュメント型が含まれる、テーブルの型列を指定します。 この型列には、特定の行のドキュメントのユーザー指定ファイル拡張子 (".doc"、".xls" など) が格納されます。 Full-Text Engine では、特定の行のファイル拡張子を使用して、その行のデータを解析するために使用する正しいフィルターを呼び出します。 その行のバイナリ データをフィルターが解析した後、指定されたワード ブレーカーがコンテンツを解析します (この例では、英語 (U.K.) のワード ブレーカーを使用します)。 フィルター処理が行われるのは、インデックス作成時か、フルテキスト インデックスへの自動変更追跡が有効になっている場合にユーザーがベース テーブルで列を挿入または列を更新したときだけである点に注意してください。 詳細については、「[検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)」を参照してください。  
  
   
## フルテキスト カタログを作成する  
  
-   [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)  
  
-   [フルテキスト カタログの作成と管理](../../relational-databases/search/create-and-manage-full-text-catalogs.md)  
  
## インデックスを表示する  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
## 一意のインデックスを作成する  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
-   [テーブル デザイナーを開く &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-table-designer-visual-database-tools.md)  
  
## フルテキスト インデックスを作成する  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)  
  
-   [フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)  
  
## フルテキスト インデックスに関する情報を表示する  
  
|カタログ ビューまたは動的管理ビュー|説明|  
|----------------------------------------|-----------------|  
|[sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)|フルテキスト カタログからフルテキスト インデックスへの参照ごとに 1 行のデータを返します。|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|フルテキスト インデックスの一部となっている列ごとに 1 行のデータを格納します。|  
|[sys.fulltext_index_fragments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)|フルテキスト インデックスでは、フルテキスト インデックス フラグメントと呼ばれる内部テーブルを使用して逆インデックスのデータを保存します。 このビューを使用すると、これらのフラグメントに関するメタデータをクエリできます。 このビューは、フルテキスト インデックスが含まれているすべてのテーブルのフルテキスト インデックス フラグメントごとに 1 行のデータを格納しています。|  
|[sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)|表形式オブジェクトのフルテキスト インデックスごとに 1 行のデータを保持します。|  
|[sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)|指定されたテーブルのフルテキスト インデックスのコンテンツに関する情報を返します。|  
|[sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)|指定されたテーブルについて、フルテキスト インデックスのドキュメント レベルのコンテンツに関連する情報を返します。 個々のキーワードは、複数のドキュメントに出現する場合があります。|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|現在実行中の、フルテキスト インデックス設定に関する情報を返します。|  
  

  
## その他の情報 
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)   
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)  
  
  