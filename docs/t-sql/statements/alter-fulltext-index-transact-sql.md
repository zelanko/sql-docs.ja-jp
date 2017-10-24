---
title: "ALTER FULLTEXT INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER FULLTEXT INDEX
- ALTER_FULLTEXT_INDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- modifying full-text indexes
- full-text indexes [SQL Server], modifying
- search property lists [SQL Server], associating with full-text indexes
- ALTER FULLTEXT INDEX statement
ms.assetid: b6fbe9e6-3033-4d1b-b6bf-1437baeefec3
caps.latest.revision: 95
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 48861e0c85263e98333ea3fad6a4da0fa0674b1f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-fulltext-index-transact-sql"></a>ALTER FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト インデックスのプロパティを変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER FULLTEXT INDEX ON table_name  
   { ENABLE   
   | DISABLE  
   | SET CHANGE_TRACKING [ = ] { MANUAL | AUTO | OFF }  
   | ADD ( column_name   
           [ TYPE COLUMN type_column_name ]   
           [ LANGUAGE language_term ]  
           [ STATISTICAL_SEMANTICS ]  
           [,...n]   
         )  
     [ WITH NO POPULATION ]  
   | ALTER COLUMN column_name  
     { ADD | DROP } STATISTICAL_SEMANTICS  
     [ WITH NO POPULATION ]  
   | DROP ( column_name [,...n] )  
     [ WITH NO POPULATION ]   
   | START { FULL | INCREMENTAL | UPDATE } POPULATION  
   | {STOP | PAUSE | RESUME } POPULATION   
   | SET STOPLIST [ = ] { OFF| SYSTEM | stoplist_name }  
     [ WITH NO POPULATION ]   
   | SET SEARCH PROPERTY LIST [ = ] { OFF | property_list_name }  
     [ WITH NO POPULATION ]   
   }  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *table_name*  
 フルテキスト インデックスに含まれている列を格納するテーブルまたはインデックス付きビューの名前を指定します。 データベース名とテーブル所有者名の指定は省略可能です。  
  
 ENABLE | DISABLE  
 指示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フル テキストを収集するかどうかのインデックス データ*table_name*です。 ENABLE はフルテキスト インデックスをアクティブにし、DISABLE はフルテキスト インデックスをオフにします。 テーブルのインデックスが無効な場合、フルテキスト クエリはサポートされません。  
  
 フルテキスト インデックスを無効にすると、変更の追跡が無効になりますが、フルテキスト インデックスは維持されます。ENABLE を使用することで、いつでもフルテキスト インデックスを有効に戻すことができます。 フルテキスト インデックスがオフになると、フルテキスト インデックス メタデータはシステム テーブル内に残ります。 フルテキスト インデックスがオフのときに CHANGE_TRACKING がオンの状態の場合 (自動または手動更新)、インデックスの状態が停止し、処理中のクロールが停止し、テーブル データへの新しい変更はインデックスに対して追跡または反映されません。  
  
 SET CHANGE_TRACKING {MANUAL | AUTO | OFF}   
 によって、フルテキスト インデックスで対応されるテーブルの列に加えられた変更 (更新、削除、または挿入) が反映されるかどうかを指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト インデックスにします。 WRITETEXT および UPDATETEXT によるデータの変更は、フルテキスト インデックスには反映されず、変更の監視でも取得されません。  
  
> [!NOTE]  
>  変更の追跡と WITH NO POPULATION の相関関係については、後の「解説」を参照してください。  
  
 MANUAL  
 ALTER FULLTEXT INDEX を呼び出すことによって、追跡された変更を手動で伝達されることを指定しています. START UPDATE POPULATION[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント (*手動作成*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用すると、この [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを定期的に呼び出すことができます。  
  
 AUTO  
 ベース テーブルでデータが変更されたとに、追跡された変更を自動的に反映されることを指定します (*自動作成*)。 この場合、フルテキスト インデックスに対して変更は自動的に反映されますが、反映までに少し時間がかかることがあります。 AUTO は既定値です。  
  
 OFF  
 指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックス付きのデータへの変更の一覧が維持されません。  
  
 追加 |DROP *column_name*  
 フルテキスト インデックスに対して追加または削除する列を指定します。 型の列または列があります**char**、 **varchar**、 **nchar**、 **nvarchar**、**テキスト**、 **ntext**、**イメージ**、 **xml**、 **varbinary**、または**varbinary (max)**です。  
  
 DROP 句は、フルテキスト インデックスが既に有効になっている列でのみ使用します。  
  
 これらのプロパティを設定する、TYPE COLUMN および LANGUAGE を ADD 句と一緒に使用して、 *column_name*です。 列を追加する場合、この列に対するフルテキスト クエリが機能するように、テーブル上のフルテキスト インデックスを再作成する必要があります。  
  
> [!NOTE]  
>  列がフルテキスト インデックスに対して追加または削除された後、フルテキスト インデックスが作成されるかどうかは、変更の追跡が有効になっているかどうかと WITH NO POPULATION が指定されているかどうかによって決まります。 詳細については、後の「解説」を参照してください。  
  
 型の列*type_column_name*  
 テーブルの列の名前を指定*type_column_name*、つまりドキュメント型を保持するために使用される、 **varbinary**、 **varbinary (max)**、または**イメージ**ドキュメント。 型列と呼ばれるこの列には、ユーザー指定のファイル拡張子 (.doc、.pdf、.xls など) が格納されます。 型列は、 **char**型、 **nchar**型、 **varchar**型、 **nvarchar**型にする必要があります。  
  
 型の列を指定*type_column_name*場合にのみ、 *column_name*を指定します、 **varbinary**、 **varbinary (max)**または**イメージ**列、データのバイナリ データとして格納される、それ以外の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。  
  
> [!NOTE]  
>  インデックスの作成時に、Full-text Engine を使用して、省略形で各テーブル行の型の列でドキュメントを使用するフルテキスト検索フィルターを特定*column_name*です。 フィルターはドキュメントをバイナリ ストリームとして読み込み、書式設定情報を削除し、ドキュメントからワード ブレーカー コンポーネントへテキストを送信します。 詳細については、「 [検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)」を参照してください。  
  
 言語*language_term*  
 格納されたデータの言語は、 **column_name**です。  
  
 *language_term*を省略して、文字列、整数、または言語のロケール識別子 (LCID) に対応する 16 進数の値として指定できます。 場合*language_term*を指定すると、その言語は検索条件のすべての要素に適用されます。 値が指定されていない場合の既定のフルテキスト言語、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを使用します。  
  
 使用して、 **sp_configure**ストアド プロシージャの既定のフルテキスト言語に関する情報にアクセスする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 文字列として指定すると*language_term*に対応する、**エイリアス**列の値、 **syslanguages**システム テーブル。 文字列は、ように、単一引用符で囲む必要があります '*language_term*' です。 整数として指定すると*language_term*言語を識別する実際の LCID です。 16 進数の値として指定する*language_term*は 0 x 後に LCID の 16 進値です。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。  
  
 値を 2 バイト文字セット (DBCS) の形式で指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で Unicode に変換されます。  
  
 指定した言語のワード ブレーカーとステミング機能などのリソースを有効にする必要があります*language_term*です。 このようなリソースは、指定した言語をサポートしていない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。  
  
 列のデータ型が BLOB および XML 以外で、複数の言語のテキスト データが含まれている場合や、列に格納されているテキストの言語が不明な場合は、ニュートラル (0x0) 言語リソースを使用します。 データ型が XML または BLOB の列に格納されているドキュメントに対しては、そのドキュメントの言語のエンコードがインデックス作成時に使用されます。 たとえば、データ型が XML の列では、XML ドキュメントの属性 xml:lang によって言語が決定されます。 クエリ時に、以前指定した値で*language_term*しない限り、フルテキスト クエリに使用される既定の言語になります*language_term*フルテキスト クエリの一部として指定されます。  
  
 STATISTICAL_SEMANTICS  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 キー フレーズを追加で作成し、統計的セマンティック インデックス作成の一部である類似性のインデックスを記録します。 詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)」を参照してください。  
  
 [ **、***...n*]  
 複数の列を ADD、ALTER、または DROP 句に指定できることを表します。 複数の列を指定する場合は、これらの列をコンマで区切ります。  
  
 WITH NO POPULATION  
 ADD または DROP 列操作、あるいは SET STOPLIST 操作後に、フルテキスト インデックスを作成しないことを指定します。 ユーザーが START...POPULATION コマンドを実行する場合のみ、フルテキスト インデックスが作成されます。  
  
 NO POPULATION を指定した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではインデックスに対して値は設定されません。 インデックスに対して値が設定されるのは、ユーザーが ALTER FULLTEXT INDEX...START POPULATION コマンドを指定した場合のみです。 NO POPULATION を指定しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではインデックスへの値が設定されます。  
  
 CHANGE_TRACKING が有効で、WITH NO POPULATION が指定されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はエラーを返します。 CHANGE_TRACKING が有効になっており、WITH NO POPULATION が指定されていない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックスで完全作成を実行します。  
  
> [!NOTE]  
>  変更の追跡と WITH NO POPULATION の相関関係の詳細については、後の「解説」を参照してください。  
  
 {ADD | DROP } STATISTICAL_SEMANTICS  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 指定された列に対する統計的セマンティック インデックス作成を有効または無効にします。 詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)」を参照してください。  
  
 START {FULL|INCREMENTAL|UPDATE} POPULATION  
 指示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のフルテキスト インデックスの作成を開始する*table_name*です。 場合は、フルテキスト インデックスの作成が既に進行中、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]警告を返し、新しいインデックスの作成を開始できません。  
  
 FULL  
 行に対してインデックスが既に作成されていても、フルテキスト インデックス作成でテーブルのすべての行が取得されます。  
  
 INCREMENTAL   
 最後の作成以降に変更された行のみがフルテキスト インデックス作成で取得されます。 INCREMENTAL は、テーブルに **timestamp**型の列がある場合にのみ適用できます。 フルテキスト カタログ内のテーブルには、型の列が含まれていない場合**タイムスタンプ**テーブルで完全作成が行われます。  
  
 UPDATE  
 変更の監視インデックスが最後に更新されてから行われた、すべての挿入、更新、削除の処理を指定します。 変更の監視の作成はテーブルで有効になっている必要がありますが、バックグラウンド更新インデックスまたは自動の変更の監視はオンにしないでください。  
  
 {STOP | PAUSE | RESUME } POPULATION   
 進行中の作成を停止または一時停止します。あるいは、一時停止中の作成を停止または再開します。  
  
 STOP POPULATION によって、自動の変更の監視またはバックグラウンド更新インデックスは停止しません。 変更の監視を停止するには、SET CHANGE_TRACKING OFF を使用します。  
  
 PAUSE POPULATION と RESUME POPULATION は完全作成に対してのみ使用できます。 他の作成では停止した場所からクロールを再開するため、他の作成の種類の場合、これらのオプションは関与しません。  
  
 セットのストップ リスト {オフ |システム |*stoplist_name* }  
 インデックスが存在する場合、そのインデックスに関連付けられているフルテキスト ストップリストを変更します。  
  
 OFF  
 フルテキスト インデックスにストップリストを関連付けないことを指定します。  
  
 SYSTEM  
 このフルテキスト インデックスに対して既定のフルテキスト システム ストップリストを使用することを指定します。  
  
 *stoplist_name*  
 フルテキスト インデックスに関連付けるストップリストの名前を指定します。  
  
 詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。  
  
 セット検索プロパティ リスト {オフ |*property_list_name* } [WITH NO POPULATION]  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 インデックスが存在する場合、そのインデックスに関連付けられている検索プロパティ リストを変更します。  
  
 OFF  
 フルテキスト インデックスにプロパティ リストを関連付けないことを指定します。 フル テキスト インデックス (ALTER FULLTEXT INDEX... の検索プロパティ リストを無効にする場合 セット検索プロパティ リスト OFF)、ベース テーブルでプロパティの検索が可能ではなくなりました。  
  
 既定では、既存の検索プロパティ リストを無効にすると、フルテキスト インデックスが自動的に再作成されます。 検索プロパティ リストを無効にするときに WITH NO POPULATION を指定した場合、自動再作成は行われません。 ただし、都合のよいときにこのフルテキスト インデックスの完全作成を実行することをお勧めします。 フルテキスト インデックスを再作成すると、削除された各検索プロパティのプロパティ固有メタデータが削除されます。その結果、フルテキスト インデックスのサイズが小さくなり効率化します。  
  
 *property_list_name*  
 フルテキスト インデックスに関連付ける検索プロパティ リストの名前を指定します。  
  
 検索プロパティ リストをフルテキスト インデックスに追加するには、インデックスの再作成を行い、関連付けられている検索プロパティ リストに登録される検索プロパティのインデックスを作成する必要があります。 検索プロパティ リストを追加するときに WITH NO POPULATION を指定した場合は、適切なタイミングでインデックスを作成する必要があります。  
  
> [!IMPORTANT]  
>  フルテキスト インデックスが以前に別の検索に関連付けられていた場合、インデックスを一貫性のある状態にするには、プロパティ リストを再構築する必要があります。 インデックスは即座に切り捨てられ、完全作成が実行されるまで空になります。 検索プロパティ リストの変更によってインデックスが再構築される場合の詳細については、このトピックの「解説」を参照してください。  
  
> [!NOTE]  
>  特定の検索プロパティ リストを同じデータベース内の複数のフルテキスト インデックスに関連付けることができます。  
  
 **現在のデータベース上に一覧表示、検索プロパティを検索するには**  
  
-   [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 検索プロパティ リストの詳細については、次を参照してください。[検索プロパティ リストとドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)です。  
  
## <a name="interactions-of-change-tracking-and-no-population-parameter"></a>変更の追跡と NO POPULATION パラメーターの相関関係  
 フルテキスト インデックスが作成されるかどうかは、変更の追跡が有効になっているかどうかと、ALTER FULLTEXT INDEX ステートメントで WITH NO POPULATION が指定されているかどうかによって決まります。 次の表は、その相関関係の結果をまとめたものです。  
  
|変更の追跡|WITH NO POPULATION|結果|  
|---------------------|------------------------|------------|  
|有効ではない|指定なし|インデックスで完全作成が実行されます。|  
|有効ではない|[Specified]|ALTER FULLTEXT INDEX...START POPULATION ステートメントが実行されるまで、インデックスの作成は行われません。|  
|有効|指定あり|エラーが発生し、インデックスは変更されません。|  
|有効|指定なし|インデックスで完全作成が実行されます。|  
  
 詳細については、フルテキスト インデックスを設定する、次を参照してください。 [、フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)です。  
  
## <a name="changing-the-search-property-list-causes-rebuilding-the-index"></a>検索プロパティ リストの変更によるインデックスの再構築  
 フルテキスト インデックスを検索プロパティ リストに初めて関連付けるときには、プロパティに固有の検索語句のインデックスを作成するためにインデックスを再作成する必要があります。 既存のインデックス データの切り捨ては行われません。  
  
 ただし、フルテキスト インデックスを別のプロパティ リストに関連付けると、インデックスが再構築されます。 再構築によりフルテキスト インデックスが即座に切り捨てられ、既存のデータがすべて削除されるため、インデックスの再作成が必要です。 カタログの作成の進行状況に応じて、フルテキスト クエリで、ベース テーブルのみで検索、カタログの作成が既に作成されているテーブル行の中にします。 再作成されるインデックス データには、新たに追加された検索プロパティ リストの登録済みプロパティのメタデータが含まれます。  
  
 再構築が行われるシナリオの例を以下に示します。  
  
-   別の検索プロパティ リストに直接切り替える場合 (このセクションの「シナリオ A」を参照)  
  
-   検索プロパティ リストを無効にし、インデックスを任意の検索プロパティ リストに関連付ける場合 (このセクションの「シナリオ B」を参照)  
  
> [!NOTE]  
>  検索プロパティ リストとフルテキスト検索のしくみの詳細については、次を参照してください。[検索プロパティ リストとドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)です。 完全作成の詳細については、次を参照してください。 [、フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)です。  
  
### <a name="scenario-a-switching-directly-to-a-different-search-property-list"></a>シナリオ A: 別の検索プロパティ リストに直接切り替える場合  
  
1.  フルテキスト インデックスを作成`table_1`を検索プロパティ リスト`spl_1`:  
  
    ```  
    CREATE FULLTEXT INDEX ON table_1 (column_name) KEY INDEX unique_key_index   
       WITH SEARCH PROPERTY LIST=spl_1,   
       CHANGE_TRACKING OFF, NO POPULATION;   
    ```  
  
2.  フルテキスト インデックスの完全作成が実行されます。  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1 START FULL POPULATION;  
    ```  
  
3.  この後フルテキスト インデックスは、次のステートメントを使用して別の検索プロパティ リスト `spl_2` に関連付けられます。  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1 SET SEARCH PROPERTY LIST spl_2;  
    ```  
  
     このステートメントにより、完全作成が実行されます。これは既定の動作です。  ただし、この処理を開始する前に、Full-Text Engine によりインデックスが自動的に切り捨てられます。  
  
### <a name="scenario-b-turning-off-the-search-property-list-and-later-associating-the-index-with-any-search-property-list"></a>シナリオ B: 検索プロパティ リストを無効にし、インデックスを任意の検索プロパティ リストに関連付ける場合  
  
1.  フルテキスト インデックスを作成`table_1`を検索プロパティ リスト`spl_1`、その後に自動の完全作成 (既定の動作)。  
  
    ```  
    CREATE FULLTEXT INDEX ON table_1 (column_name) KEY INDEX unique_key_index   
       WITH SEARCH PROPERTY LIST=spl_1;   
    ```  
  
2.  次に示すように、検索プロパティ リストが無効になります。  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1   
       SET SEARCH PROPERTY LIST OFF WITH NO POPULATION;   
    ```  
  
3.  フルテキスト インデックスが同じ検索プロパティ リストまたは別の検索プロパティ リストにもう一度関連付けられます。  
  
     たとえば、次のステートメントの関連付けを再、フルテキスト インデックスを元の検索プロパティ リスト`spl_1`:  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1 SET SEARCH PROPERTY LIST spl_1;  
    ```  
  
     このステートメントにより、完全作成が開始されます。これは既定の動作です。  
  
    > [!NOTE]  
    >  など、別の検索プロパティ リストの再構築が必要も、`spl_2`です。  
  
## <a name="permissions"></a>Permissions  
 ユーザーがテーブルまたはインデックス付きビューに対する ALTER 権限を持っているかのメンバーである必要があります、 **sysadmin**固定サーバー ロール、または**db_ddladmin**または**db_owner**固定データベース ロール.  
  
 SET STOPLIST を指定した場合は、ユーザーがそのストップリストに対する REFERENCES 権限を持っている必要があります。 SET SEARCH PROPERTY LIST を指定した場合は、ユーザーが検索プロパティ リストに対する REFERENCES 権限を持っている必要があります。 指定したストップリストまたは検索プロパティ リストの所有者は、ALTER FULLTEXT CATALOG 権限を持っている場合、REFERENCES 権限を許可できます。  
  
> [!NOTE]  
>  一般のユーザーには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に含まれる既定のストップリストに対する REFERENCES 権限が許可されています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-manual-change-tracking"></a>A. 手動の変更追跡を設定する  
 次の例では、`JobCandidate` テーブルで、フルテキスト インデックスに対して手動での変更追跡を設定します。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate  
   SET CHANGE_TRACKING MANUAL;  
GO  
```  
  
### <a name="b-associating-a-property-list-with-a-full-text-index"></a>B. プロパティ リストをフルテキスト インデックスに関連付ける  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の使用例、`DocumentPropertyList`プロパティ リスト フルテキスト インデックスを持つ、`Production.Document`テーブル。 この ALTER FULLTEXT INDEX ステートメントにより、完全作成が開始されます。これは、SET SEARCH PROPERTY LIST 句の既定の動作です。  
  
> [!NOTE]  
>  作成する例については、`DocumentPropertyList`プロパティ リストを参照してください[CREATE SEARCH PROPERTY LIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST DocumentPropertyList;   
GO  
```  
  
### <a name="c-removing-a-search-property-list"></a>C. 検索プロパティ リストを削除する  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例では、`DocumentPropertyList` でフルテキスト インデックスから `Production.Document` プロパティ リストを削除します。 この例では、インデックスからプロパティをすぐに削除する必要はないため、WITH NO POPULATION オプションが指定されています。 ただし、このフルテキスト インデックスに対するプロパティ レベルの検索は実行できなくなります。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST OFF WITH NO POPULATION;   
GO  
```  
  
### <a name="d-starting-a-full-population"></a>D. 完全作成を開始する  
 次の例で、フルテキスト インデックスに full population を開始する、`JobCandidate`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate   
   START FULL POPULATION;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_indexes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)  
  
  

