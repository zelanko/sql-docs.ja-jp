---
title: フルテキスト検索の動作の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- behavior changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: 573444e8-51bc-4f3d-9813-0037d2e13b8f
author: rothja
ms.author: jroth
ms.openlocfilehash: cbe807237651bd8bb81fa1c9f028847654b97889
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936181"
---
# <a name="behavior-changes-to-full-text-search"></a>フルテキスト検索の動作の変更
  このトピックでは、フルテキスト検索の動作変更について説明します。 動作変更によって、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の機能や操作方法が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の以前のバージョンと異なっています。  
  
## <a name="behavior-changes-in-full-text-search-in-sssql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] におけるフルテキスト検索の動作の変更  
 今後、情報が追加されていきます。  
  
## <a name="behavior-changes-in-full-text-search-in-sssql11"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] におけるフルテキスト検索の動作の変更  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、アメリカ英語 (LCID 1033) とイギリス英語 (LCID 2057) 用に新しいバージョンのワード ブレーカーとステミング機能がインストールされます。 ただし、以前の動作を維持する場合は、これらのコンポーネントの以前のバージョンに切り替えることができます。 詳細については、「 [米国英語と英国英語に使用されるワード ブレーカーを変更する方法](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md)」を参照してください。  
  
### <a name="new-word-breakers-and-stemmers-installed"></a>新しいワード ブレーカーとステミング機能のインストール  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、フルテキスト検索とセマンティック検索で使用されるすべてのワード ブレーカーおよびステミング機能が更新されます。 インデックスのコンテンツとクエリの結果の一貫性を保つために、既存のフルテキスト インデックスを再作成することをお勧めします。  
  
1.  英語向けの新しいワード ブレーカーがあります。 以前の動作を維持する必要がある場合は、「 [米国英語と英国英語に使用されるワード ブレーカーの変更](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md)」を参照してください。  
  
2.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の以前のリリースに含まれていたデンマーク語、ポーランド語、およびトルコ語向けのサードパーティ製のワード ブレーカーは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] コンポーネントに置き換えられました。 新しいコンポーネントは既定で有効になっています。  
  
3.  チェコ語とギリシャ語向けの新しいワード ブレーカーがあります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] フルテキスト検索の以前のリリースでは、これらの 2 つの言語のサポートは含まれていません。  
  
### <a name="behavior-changes-of-new-word-breakers-and-stemmers"></a>新しいワード ブレーカーとステミング機能の動作の変更  
 新しいコンポーネントでは、フルテキスト インデックスを作成してクエリを行ったときに、古いコンポーネントとは異なる結果が返されることがあります。 次の表は、英語の結果で予想される相違点を示しています。  
  
 ワード ブレーカーとステミング機能の以前の動作を維持する必要がある場合は、次のトピックを参照してください。  
  
-   [米国英語と英国英語に使用されるワード ブレーカーを変更する方法](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md)  
  
-   [検索で使用するワード ブレーカーを以前のバージョンに戻す](../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)  
  
 新しいコンポーネントは、次のような *詳細* な結果を返す場合があります。  
  
|**用語**|**ワード ブレーカーとステミング機能が以前のバージョンの場合の結果**|**ワード ブレーカーとステミング機能が新しい場合の結果**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|cat-dog|cat<br /><br /> dog|cat<br /><br /> cat-dog<br /><br /> dog|  
|cat@dog.com|cat<br /><br /> com<br /><br /> dog|cat<br /><br /> cat@dog.com<br /><br /> com<br /><br /> dog|  
|12/11/2011<br /><br /> *(用語は日付です)*|12/11/2011<br /><br /> dd20111211|11<br /><br /> 12<br /><br /> 12/11/2011<br /><br /> 2011<br /><br /> dd20111211|  
  
 新しいコンポーネントは、次のような *類似した* 結果を返す場合があります。  
  
|**用語**|**ワード ブレーカーとステミング機能が以前のバージョンの場合の結果**|**ワード ブレーカーとステミング機能が新しい場合の結果**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|100$|100$<br /><br /> nn100$|100$<br /><br /> nn100usd|  
|022|022<br /><br /> nn022|022<br /><br /> nn22|  
|10:49AM<br /><br /> *(用語は時刻です)*|10:49AM<br /><br /> tt1049|10:49AM<br /><br /> tt24104900|  
  
 新しいコンポーネントは、次のような *少数* の結果またはアプリケーションで予期できない結果を返す場合があります。  
  
|**用語**|**ワード ブレーカーとステミング機能が以前のバージョンの場合の結果**|**ワード ブレーカーとステミング機能が新しい場合の結果**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|jěˊÿｑℭžl<br /><br /> *(用語が、有効な英語の文字ではありません)*|'jěˊÿｑℭžl'|je yq zl|  
|table's|table's<br /><br /> table|table's|  
|cat-|cat<br /><br /> cat-|cat|  
|v-z *(v と z はノイズ ワードです)*|*(結果なし)*|v-z|  
|$100 000 USD|$100<br /><br /> 000<br /><br /> nn000<br /><br /> nn100$<br /><br /> usd|$100 000 USD<br /><br /> nn100000usd|  
|beautiful U.S land|beautiful<br /><br /> land<br /><br /> u.s<br /><br /> us|beautiful<br /><br /> land|  
|Mt. Kent and Mt Challenger|challenger<br /><br /> kent<br /><br /> mt<br /><br /> Mt.|mt<br /><br /> kent<br /><br /> challenger|  
  
## <a name="behavior-changes-in-full-text-search-in-sql-server-2008"></a>SQL Server 2008 でのフルテキスト検索の動作の変更  
 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]以降のバージョンでは、フルテキストエンジンは、サーバークエリおよびストレージエンジンインフラストラクチャの一部として、リレーショナルデータベースにデータベースサービスとして統合されています。 フルテキスト検索の新しいアーキテクチャにより、次の目的が達成されます。  
  
-   統合ストレージと管理-フルテキスト検索は、の固有のストレージおよび管理機能と直接統合され、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] MSFTESQL サービスは存在しなくなりました。  
  
    -   フルテキスト インデックスが、ファイル システム内ではなくデータベース ファイル グループ内に格納されます。 バックアップの作成など、データベースに対する管理操作は、自動的にフルテキスト インデックスにも影響します。  
  
    -   フルテキストカタログは、ファイルグループに属さない仮想オブジェクトになりました。これは、フルテキストインデックスのグループを指す論理的概念です。 そのため、多くのカタログ管理機能が非推奨とされた結果、一部の機能に重大な変更が生じています。 詳細については、「 [SQL Server 2014 の非推奨のデータベースエンジン機能](deprecated-database-engine-features-in-sql-server-2016.md)」および「[フルテキスト検索の重大な変更](breaking-changes-to-full-text-search.md)」を参照してください。  
  
        > [!NOTE]  
        >  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)][!INCLUDE[tsql](../includes/tsql-md.md)]フルテキストカタログを指定する DDL ステートメントは正常に機能します。  
  
-   クエリ処理の統合-新しいフルテキスト検索クエリプロセッサは、データベースエンジンの一部であり、SQL Server クエリプロセッサと完全に統合されています。 このため、クエリ オプティマイザーはフルテキスト クエリ述語を認識し、自動的に最も効率的に実行します。  
  
-   高度な管理とトラブルシューティング-統合フルテキスト検索では、フルテキストインデックス、特定のワードブレーカーの出力、ストップワード構成などの検索構造の分析に役立つツールが用意されています。  
  
-   ノイズ ワードとノイズ ワード ファイルが、ストップワードとストップリストに置き換えられました。 ストップリストは、ストップワードの管理タスクを容易にし、異なるサーバー インスタンスや環境間の整合性を向上させるデータベース オブジェクトです。 詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。  
  
-   [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョンには、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] に存在する言語のうち、多くの言語に対する新しいワード ブレーカーが含まれています。 変更がないのは、英語、韓国語、タイ語、中国語 (すべての形式) のワード ブレーカーだけです。 その他の言語では、データベースを以降のバージョンにアップグレードしたときにフルテキストカタログがインポートされた場合、フルテキスト [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] カタログのフルテキストインデックスで使用される1つ以上の言語が、インポートされたワードブレーカーとは少し異なる動作をする新しいワードブレーカーに関連付けられるようになりました。 クエリとフルテキストインデックスコンテンツの一貫性を確保する方法の詳細については、「[フルテキスト検索のアップグレード](../relational-databases/search/upgrade-full-text-search.md)」を参照してください。  
  
-   新しい FDHOST ランチャー (MSSQLFDLauncher) サービスが追加されました。 詳細については、「[フルテキスト検索の概要](../relational-databases/search/get-started-with-full-text-search.md)」を参照してください。  
  
-   フルテキストインデックス作成は、列と同じように[FILESTREAM](../relational-databases/blob/filestream-sql-server.md)列で動作し `varbinary(max)` ます。 FILESTREAM テーブルに、各 FILESTREAM BLOB のファイル名拡張子を含む列が含まれている必要があります。 詳細については、「[フルテキスト検索を使用したクエリ](../relational-databases/search/query-with-full-text-search.md)」、「[検索用フィルターの構成と管理](../relational-databases/search/configure-and-manage-filters-for-search.md)」、および「 [fulltext_document_types &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)」を参照してください。  
  
     フルテキスト エンジンは、FILESTREAM BLOB の内容のインデックスを作成します。 イメージなど、インデックスを作成しても役に立たないファイルもあります。 FILESTREAM BLOB が更新されると、インデックスが再作成されます。  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索](../relational-databases/search/full-text-search.md)   
 [フルテキスト検索の旧バージョンとの互換性](../../2014/database-engine/full-text-search-backward-compatibility.md)   
 [フルテキスト検索のアップグレード](../relational-databases/search/upgrade-full-text-search.md)   
 [フルテキスト検索の概要](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
