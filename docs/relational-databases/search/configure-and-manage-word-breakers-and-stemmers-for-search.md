---
title: "検索用のワード ブレーカーとステミング機能の構成と管理 | Microsoft Docs"
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
  - "言語 [フルテキスト検索]"
  - "フルテキスト検索 [SQL Server], ステマー"
  - "言語分析 [フルテキスト検索]"
  - "フルテキスト インデックス [SQL Server], 言語分析"
  - "フルテキスト検索 [SQL Server], ワード ブレーカー"
  - "[既定のフルテキスト言語] オプション"
  - "ステミング機能 [フルテキスト検索]"
  - "動詞の活用 [フルテキスト検索]"
  - "ワード ブレーカー [フルテキスト検索]"
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
caps.latest.revision: 89
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 88
---
# 検索用のワード ブレーカーとステミング機能の構成と管理
  ワード ブレーカーとステミング機能は、すべてのフルテキスト インデックス データに対して言語分析を実行します。 言語分析には、単語の境界 (単語の区切り) の検索と動詞の活用 (ステミング) が含まれます。 ワード ブレーカーとステミング機能は言語に固有のものであり、言語分析の規則は言語によって異なります。 特定の言語において、*ワード ブレーカー*によって、言語の語彙の規則に基づいて単語の境界を検出し、個々の単語を識別します。 各単語 (*トークン*ともいいます) は、サイズを縮小するために圧縮された表現でフルテキスト インデックスに挿入されます。 *ステミング機能*はその言語の規則に基づいて特定の語の変化形を生成します (たとえば、"running"、"ran"、"runner" は、"run" という語の変化形です)。  
  
 言語固有のワード ブレーカーを使用すると、その言語に対する検索結果の精度が高くなります。 言語ファミリにはワード ブレーカーが存在していても、特定のサブ言語は対象とされない場合は、主言語が使用されます。 たとえば、カナダ系フランス語テキストの処理には、フランス語のワード ブレーカーが使用されます。 特定の言語用のワード ブレーカーが使用できない場合は、ニュートラル ワード ブレーカーが使用されます。 ニュートラル ワード ブレーカーを使用すると、単語は空白や句読点などのニュートラル文字で分割されます。  
  
##  <a name="register"></a> ワード ブレーカーの登録  
 言語のワード ブレーカーを使用する場合は、そのワード ブレーカーを登録する必要があります。 ワード ブレーカーを登録すると、関連する言語リソース (ステミング機能、ノイズ ワード (ストップワード)、および類義語辞典ファイル) もフルテキスト インデックス操作やフルテキスト クエリ操作で使用できるようになります。 現在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にワード ブレーカーが登録されている言語の一覧を表示するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
 SELECT * FROM sys.fulltext_languages  
  
 ワード ブレーカーを追加、削除、または変更すると、フルテキスト インデックスおよびフルテキスト クエリでサポートされている Microsoft Windows のロケール識別子 (LCID) の一覧を更新する必要があります。 詳細については、「 [View or Change Registered Filters and Word Breakers](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)」を参照してください。  
  
##  <a name="default"></a> [既定のフルテキスト言語] オプションの設定  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズされたバージョンでは、適切な言語が存在する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによって **default full-text language** オプションはサーバーの言語に設定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズされていないバージョンでは、**[既定のフルテキスト言語]** オプションは英語になります。  
  
 フルテキスト インデックスを作成または変更する際には、フルテキスト インデックス列ごとに言語を指定できます。 列に言語が指定されていない場合、既定では構成オプション **default full-text language** の値になります。  
  
> [!NOTE]  
>  1 つのフルテキスト クエリ関数句に指定されるすべての列は、クエリで LANGUAGE オプションが指定されていない限り、同じ言語を使用する必要があります。 クエリ対象のフルテキスト インデックスが付けられた列に使用する言語によって、フルテキスト クエリの述語 ([CONTAINS](../../t-sql/queries/contains-transact-sql.md) および [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)) および関数 ([CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) および [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md)) の引数に対して実行される言語分析が決まります。  
  
##  <a name="lang"></a> インデックス付きの列の言語の選択  
 フルテキスト インデックスを作成する際には、各インデックス列に対して言語を指定することをお勧めします。 列に言語が指定されていない場合、システムの既定の言語が使用されます。 列のインデックス作成に使用されるワード ブレーカーとステミング機能は、列の言語によって決まります。 また、指定した言語の類義語辞典ファイルが、列のフルテキスト クエリで使用されます。  
  
 フルテキスト インデックスの作成時に列の言語を選択する際には、注意点が 2 つあります。 これらの注意点は、テキストをトークン化する方法と、Full-Text Engine によるインデックス作成の方法にかかわるものです。 詳細については、「[フルテキスト インデックス作成時の言語の選択](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)」を参照してください。  
  
 **列のワード ブレーカーの言語を表示するには**  
  
-   [フルテキスト インデックスの管理](../Topic/Manage%20Full-Text%20Indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="info"></a> ワード ブレーカーの情報の取得  
 **ワード ブレーカー、類義語辞典、およびストップリストの組み合わせによるトークン化の結果の表示**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md)  
  
 **登録されているワード ブレーカーに関する情報を返すには**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
  
##  <a name="tshoot"></a> 単語区切りのタイムアウト エラーのトラブルシューティング  
 単語区切りのタイムアウト エラーは、さまざまな状況で発生する可能性があります。 エラーが発生する状況とその対処方法については、「[MSSQLSERVER_30053](../Topic/MSSQLSERVER_30053.md)」を参照してください。  
  
##  <a name="impact"></a> 新しいワード ブレーカーの影響について  
 各バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、通常、新しいワード ブレーカーが含まれています。これらのワード ブレーカーでは、言語の規則が改良されているため、以前のワード ブレーカーよりも精度が向上しています。 新しいワード ブレーカーは、前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からインポートされたフルテキスト インデックスのワード ブレーカーとは少し動作が異なる場合もあります。 データベースが現在のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードされたときにフルテキスト カタログをインポートした場合は、この動作の違いが重要になります。 フルテキスト カタログのフルテキスト インデックスで使用される 1 つまたは複数の言語が、新しいワード ブレーカーに関連付けられる可能性があります。 詳細については、「[フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)」を参照してください。  
  
 すべてのワード ブレーカーの一覧については、「[sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)」を参照してください。  
  
## 参照  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)   
 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)  
  
  