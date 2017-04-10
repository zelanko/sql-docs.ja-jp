---
title: "フルテキスト検索に使用する類義語辞典ファイルの構成と管理 | Microsoft Docs"
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
  - "類義語辞典ファイルのフルテキスト インデックス [SQL Server]"
  - "類義語辞典 [フルテキスト検索], 構成"
  - "類義語辞典 [フルテキスト検索]"
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
caps.latest.revision: 84
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 83
---
# フルテキスト検索に使用する類義語辞典ファイルの構成と管理
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではフルテキスト クエリで類義語辞典を使用し、指定した用語のシノニムを検索できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の*類義語辞典*では、特定の言語の一連のシノニムを定義します。 システム管理者は、拡張セットと置換セットという 2 つの形式のシノニムを定義できます。 フルテキスト データに合わせた類義語辞典を作成すると、そのデータのフルテキスト クエリのスコープを効果的に拡張できます。 類義語辞典の照合は、FORMSOF THESAURUS 句を指定する [CONTAINS](../../t-sql/queries/contains-transact-sql.md) クエリと [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) クエリの場合、およびすべての [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) クエリと [FREETEXTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) クエリの場合に行われます。  
  
##  <a name="tasks"></a> 類義語辞典ファイルを設定するための基本的なタスク  
 サーバー インスタンス上のフルテキスト検索クエリで特定の言語のシノニムを検索するには、その言語の類義語辞典のマッピング (シノニム) を定義しておく必要があります。 各類義語辞典は、次の内容を定義するために手動で構成する必要があります。  
  
-   分音文字の設定  
  
     類義語辞典では、チルダ (**~**)、アキュート アクセント記号 (**´**)、ウムラウト (**¨**) などの分音記号をすべての検索パターンで区別するかしないか (*アクセントを区別する*、または*アクセントを区別しない*) が設定されます。 たとえば、フルテキスト クエリで "café" というパターンが他のパターンに置き換えられるように指定するとします。 類義語辞典でアクセントが区別されない場合、フルテキスト検索では、パターン "café" と "cafe" が置き換えられます。 類義語辞典でアクセントが区別される場合、フルテキスト検索では "café" というパターンのみが置き換えられます。 既定では、類義語辞典でアクセントは区別されません。  
  
-   拡張セット  
  
     拡張セットには、フルテキスト クエリで相互に置き換えられる "writer"、"author"、"journalist" などのシノニムのグループが格納されます。 拡張セット内のシノニムと一致するクエリは、拡張セット内の他のシノニムもすべて含むように拡張されます。  
  
     詳細については、このトピックの後半の「拡張セットの XML 構造」をご覧ください。  
  
-   置換セット  
  
     置換セットには、代替セットによって置き換えられるテキストのパターンが格納されます。 このトピックの後半で説明する「置換セットの XML 構造」の例をご覧ください。  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
##  <a name="initial_thesaurus_files"></a> 類義語辞典ファイルの初期内容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には XML 類義語辞典ファイルのセットが用意されており、サポートされている各言語に対して 1 つのファイルが存在します。 これらのファイルは基本的に空です。 すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類義語辞典およびコメント アウトされたサンプル類義語辞典に共通する最上位の XML 構造のみが格納されています。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でリリースされている類義語辞典ファイルには、すべて次の XML コードが含まれています。  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
##  <a name="location"></a> 類義語辞典ファイルの場所  
 類義語辞典ファイルの既定の場所は次のとおりです。  
  
 *<SQL_Server_data_files_path>*\MSSQL13.MSSQLSERVER\MSSQL\FTDATA\  
  
 この既定の場所には、次のファイルが格納されています。  
  
-   言語固有の類義語辞典ファイル  
  
     セットアップ中に、空の類義語辞典ファイルが前述の場所にインストールされます。 サポートされている言語ごとに個別のファイルが用意されています。 システム管理者は、これらのファイルをカスタマイズできます。  
  
     類義語辞典ファイルの既定のファイル名には、次の形式が使用されます。  
  
     ‘ts’ + \<three-letter language-abbreviation> + '.xml'  
  
     特定の言語の類義語辞典ファイルの名前は、レジストリで HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev> と指定されています。  
  
-   グローバル類義語辞典ファイル  
  
     tsGlobal.xml は空のグローバル類義語辞典ファイルです。  
  
 類義語辞典ファイルの場所および名前を変更するには、そのレジストリ キーを変更します。 各言語の類義語辞典ファイルの場所は、レジストリで次のように指定されています。  
  
 HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<instance name>/MSSearch/Language/\<language-abbreviation>/TsaurusFile  
  
 グローバル類義語辞典ファイルは、LCID 0 のニュートラル言語に対応します。 この値は、管理者のみが変更できます。  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
##  <a name="how_queries_use_tf"></a> クエリで類義語辞典ファイルを使用する方法  
 類義語辞典クエリでは、言語固有の類義語辞典とグローバル類義語辞典の両方が使用されます。 まず、言語固有のファイルが参照されて処理のために読み込まれ (まだ読み込まれていない場合)、 類義語辞典ファイル内の拡張セットおよび置換セットのルールで指定された言語固有のシノニムを含むようにクエリが拡張されます。 この手順がグローバル類義語辞典に対して繰り返されます。 ただし、言語固有の類義語辞典ファイルで既に一致するものが見つかった用語は、グローバル類義語辞典では照合されません。  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
##  <a name="structure"></a> 類義語辞典ファイルの構造について  
 各類義語辞典ファイルでは、ID が `Microsoft Search Thesaurus` の XML コンテナー、およびサンプル類義語辞典を含むコメント `<!--` … `-->`が定義されます。 類義語辞典は \<thesaurus> 要素で定義されます。この要素には、次のように分音文字の設定、拡張セット、および置換セットを定義する子要素のサンプルが含まれます。  
  
-   分音文字の設定の XML 構造  
  
     類義語辞典の分音文字の設定は、単一の <diacritics_sensitive> 要素で指定されます。 この要素には、次のようにアクセントの区別を制御する整数値が含まれます。  
  
    |分音文字の設定|値|XML|  
    |------------------------|-----------|---------|  
    |アクセントを区別しない|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |アクセントを区別する|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  この設定はファイルで 1 回のみ適用でき、ファイル内のすべての検索パターンに適用されます。 この設定は個別のパターンには指定できません。  
  
-   拡張セットの XML 構造  
  
     各拡張セットは \<expansion> 要素で囲みます。 この要素内に、\<sub> 要素で囲んだ 1 つ以上の代替文字列を指定します。 拡張セットでは、互いにシノニムとなる代替文字列のグループを指定できます。  
  
     たとえば、拡張のセクションを編集して、代替文字列 "writer"、"author"、および "journalist" をシノニムとして扱うことができます。 1 つの代替文字列と一致するフルテキスト検索クエリは、拡張セット内の他の代替文字列もすべて含むように拡張されます。 したがって、上記の例では、"author" という語に対して FORMS OF THESAURUS クエリまたは FREETEXT クエリを実行すると、フルテキスト検索では "writer" と "journalist" という語も含む検索結果が返されます。  
  
     上記の例の拡張セットのセクションを次に示します。  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   置換セットの XML 構造  
  
     各置換セットは \<replacement> 要素で囲みます。 この要素内に、\<pat> 要素で囲んだ 1 つ以上のパターン、および \<sub> 要素で囲んだ 0 個以上の代替文字列 (シノニムごとに 1 つ) を指定できます。 ここで指定するパターンが代替セットで置き換えられます。 パターンと代替文字列には、語または語の並びを含めることができます。 パターンに対して代替文字列が指定されていない場合は、ユーザー クエリからパターンが削除されます。  
  
     たとえば、"Win8" というパターンを検索するクエリを、"Windows Server 2012" または "Windows 8.0" という代替文字列に置き換えるとします。 この場合、"Win8" に対してフルテキスト クエリを実行すると、フルテキスト検索からは "Windows Server 201" または "Windows 8.0" だけを含む検索結果が返されます。 "Win8" を含む結果は返されません。 これは、"Win8" が "Windows Server 2012" と "Windows 8.0" というパターンに置換されるためです。  
  
     上記の例の置換セットのセクションを次に示します。  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     類似するパターンを含む 2 つの置換セットが一致する場合、2 つのうちで長い置換セットが優先されます。 たとえば、"Internet Explorer online community" に対して FORMS OF THESAURUS クエリを実行し、次の置換セットを使用すると、"Internet Explorer" 置換セットの方が "Internet" 置換セットよりも優先されます。 したがって、このクエリは "IE online community" または "IE 9 online community" として処理されます。  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     」および「  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
##  <a name="working_with_thesaurus_files"></a> 類義語辞典ファイルの操作  
 **類義語辞典ファイルを編集するには**  
  
-   [類義語辞典ファイルの編集](#editing)  
  
 **更新された類義語辞典ファイルを読み込むには**  
  
-   [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)  
  
 **ワード ブレーカー、類語辞典、およびストップリストの組み合わせによるトークン化の結果を表示するには**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md)  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
##  <a name="editing"></a> 類義語辞典ファイルの編集  
 特定の言語の類義語辞典は、類義語辞典ファイル (XML ファイル) を編集することによって構成できます。 セットアップ中に、\<xml> コンテナーおよびコメント アウトされたサンプルの \<thesaurus> 要素のみが格納されている空の類義語辞典ファイルがインストールされます。 シノニムを検索するフルテキスト検索クエリを正しく機能させるには、一連のシノニムを定義する実際の \<thesaurus> 要素を作成する必要があります。 シノニムの定義には、拡張セットと置換セットという 2 つの形式があります。  
  
 **類義語辞典ファイルの制限**  
  
 類義語辞典ファイルの編集には、次の制限が適用されます。  
  
-   類義語辞典ファイルを更新、変更、または削除できるのはシステム管理者だけです。  
  
-   テキスト エディター ツールを使用して類義語辞典ファイルを編集する場合、ファイルが Unicode 形式で保存され、バイト順マークが指定されている必要があります。  
  
-   類義語辞典のエントリを空にしたり、空の文字列の単語に区切ったりすることはできません。  
  
-   類義語辞典ファイルの語句は 512 文字以下にする必要があります。  
  
-   類義語辞典には、拡張セットの \<sub> エントリおよび置換セットの \<pat> 要素間で重複したエントリを含めることはできません。  
  
 **類義語辞典ファイルに関する推奨事項**  
  
 類義語辞典ファイル内のエントリには特殊文字を含めないことをお勧めします。 これは、特殊文字に対するワード ブレーカーの動作がわかりづらいためです。 類義語辞典のエントリに特殊文字が含まれる場合、そのエントリと組み合わせて使用されるワード ブレーカーの動作がフルテキスト クエリに与える影響がわかりづらくなる可能性があります。  
  
 ストップワードはフルテキスト インデックスから省略されるので、\<sub> エントリにはストップワードを含めないことをお勧めします。 クエリは類義語辞典ファイルの \<sub> エントリを含むように拡張されるので、\<sub> エントリにストップワードが含まれる場合は、クエリのサイズが不必要に大きくなります。  
  
#### 類義語辞典ファイルを編集するには  
  
1.  類義語辞典ファイルをメモ帳で開きます。  
  
2.  初めて類義語辞典ファイルを編集する場合は、ファイルの先頭と末尾の次のコメント行をそれぞれ削除します。  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  置換セットまたは拡張セットを追加、変更、または削除します。  
  
4.  ファイルを保存し、メモ帳を閉じます。  
  
5.  類義語辞典ファイルの内容を tempdb に読み込むために [sp_fulltext_load_thesaurus_file](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md) を使用し、類義語辞典ファイルの言語に対応するロケール識別子 (LCID) を指定します。 たとえば、英語の類義語辞典ファイル tsenu.xml の場合、対応する LCID は 1033 です。  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
 [&#91;先頭に戻る&#93;](#Top)  
  
## 参照  
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  