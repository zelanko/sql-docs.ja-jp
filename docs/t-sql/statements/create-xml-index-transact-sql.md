---
title: "CREATE XML INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- XML_TSQL
- CREATE_XML_INDEX_TSQL
- XML INDEX
- CREATE_XML_TSQL
- XML
- CREATE XML
- CREATE XML INDEX
- XML_INDEX_TSQL
- FOR_XML_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE XML INDEX statement
- CREATE INDEX statement
- index creation [SQL Server], XML indexes
- XML indexes [SQL Server], creating
ms.assetid: c510cfbc-68be-4736-b3cc-dc5b7aa51f14
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f9e235df8fe59bc86522ece554a75e22954fef1b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-xml-index-transact-sql"></a>CREATE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定したテーブルに XML インデックスを作成します。 インデックスはテーブル内にデータがなくても作成できます。 データベース名を修飾して指定することにより、他のデータベース内のテーブルに XML インデックスを作成することもできます。  
  
> [!NOTE]  
>  リレーショナル インデックスを作成するを参照してください。 [CREATE INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md). 空間インデックスを作成する方法については、次を参照してください。 [CREATE SPATIAL INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-spatial-index-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
Create XML Index   
CREATE [ PRIMARY ] XML INDEX index_name   
    ON <object> ( xml_column_name )  
    [ USING XML INDEX xml_index_name   
        [ FOR { VALUE | PATH | PROPERTY } ] ]  
    [ WITH ( <xml_index_option> [ ,...n ] ) ]  
[ ; ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_name  
}  
  
<xml_index_option> ::=  
{   
    PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
}  
  
```  
  
## <a name="arguments"></a>引数  
 [PRIMARY] XML  
 指定した XML インデックスを作成**xml**列です。 PRIMARY を指定した場合、クラスター化インデックスは、ユーザー テーブルのクラスター化キーと XML ノード識別子から構成されるクラスター化キーで作成されます。 各テーブルには 249 個までの XML インデックスを作成できます。 XML インデックスを作成するときには、次のことに注意してください。  
  
-   クラスター化インデックスは、ユーザー テーブルの主キー上に存在する必要がある。  
  
-   ユーザー テーブルのクラスター化キーは 15 列に制限されている。  
  
-   各**xml**テーブル内の列は、1 つのプライマリ XML インデックスと複数のセカンダリ XML インデックスを持つことができます。  
  
-   プライマリ XML インデックス、 **xml**列にセカンダリ XML インデックスを作成する前に列が存在する必要があります。  
  
-   XML インデックスは、1 つのみ作成できます**xml**列です。 以外の XML インデックスを作成することはできません**xml**リレーショナル インデックスを作成する列を使うことも、 **xml**列です。  
  
-   プライマリまたはセカンダリ XML インデックスを作成することはできません、 **xml**を持つテーブル値変数に、ビュー内の列**xml**列、または**xml**変数を入力します。  
  
-   計算で、プライマリ XML インデックスを作成することはできません**xml**列です。  
  
-   SET オプション設定は、インデックス付きビューおよび計算列インデックスに必要な設定と同じにする必要がある。 具体的には、オプション ARITHABORT 必要があります ON に設定する XML インデックスが作成されるときとで値の挿入、削除、または更新時に、 **xml**列です。  
  
 詳細については、「[XML インデックス &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)」をご覧ください。  
  
 *index_name*  
 インデックスの名前。 インデックス名は、テーブル内では一意である必要がありますが、データベース内で一意である必要はありません。 インデックス名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 プライマリ XML インデックスの名前は、次の文字を始めることはできません:  **#** 、  **##** 、  **@** 、または **@@** .  
  
 *xml_column_name*  
 **Xml**インデックスの基になる列。 1 つだけ**xml**列は、単一の XML インデックス定義で指定できます。 しかし、で複数のセカンダリ XML インデックスを作成することができます、 **xml**列です。  
  
 USING XML INDEX *xml_index_name*  
 セカンダリ XML インデックスの作成でプライマリ XML インデックスを使用します。  
  
 FOR { VALUE | PATH | PROPERTY }   
 セカンダリ XML インデックスの種類を指定します。  
  
 Value  
 キー列がプライマリ XML インデックス (ノード値とパス) となっている列に、セカンダリ XML インデックスを作成します。  
  
 PATH  
 プライマリ XML インデックスのパス値とノード値に基づく列に、セカンダリ XML インデックスを作成します。 PATH セカンダリ インデックスではパス値とノード値がキー列になり、パスの検索時に効率的にシークできるようになります。  
  
 PROPERTY  
 PK がベース テーブルの主キーとなっているプライマリ XML インデックスの列 (PK、パスおよびノード値) に、セカンダリ XML インデックスを作成します。  
  
 **\<オブジェクト >:: =**  
  
 インデックスを作成するオブジェクトを、完全修飾または完全修飾ではない形式で指定します。  
  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 テーブルが所属するスキーマの名前を指定します。  
  
 *table_name*  
 インデックスを作成するテーブルの名前を指定します。  
  
 **\<xml_index_option >:: =** 
  
 インデックスを作成するときに使用するオプションを指定します。  
  
 PAD_INDEX  **=**  {ON |**OFF** }  
 インデックスの埋め込みを指定します。 既定値は OFF です。  
  
 ON  
 によって指定される空き領域の割合*fillfactor*インデックスの中間レベル ページに適用されます。  
  
 OFF または*fillfactor*が指定されていません  
 中間レベルのページはほぼ全容量が使用されます。ただし、中間ページにあるキーのセットを考慮して、インデックスに割り当てることのできる、少なくとも 1 行の最大サイズが収まる分の領域は残されます。  
  
 PAD_INDEX では FILLFACTOR で指定されるパーセンテージが使用されるので、PAD_INDEX オプションは、FILLFACTOR が指定されている場合にのみ有効です。 FILLFACTOR で指定されるパーセンテージが 1 つの行を許可するのに十分な大きさがない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]内部的に最小値を許可する比率をオーバーライドします。 中間インデックス ページ上の行の番号 2 にはなりません未満の値をどのように低に関係なく*fillfactor*です。  
  
 FILLFACTOR  **=**  *fillfactor*  
 インデックスの作成時または再構築時に、[!INCLUDE[ssDE](../../includes/ssde-md.md)] が各インデックス ページのリーフ レベルをどの程度まで埋めるかを、パーセント値で指定します。 *fillfactor* 1 から 100 までの整数値にする必要があります。 既定値は 0 です。 場合*fillfactor*が 100 または 0 の場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]全容量リーフ ページを含むインデックスを作成します。  
  
> [!NOTE]  
>  Fill factor 値 0 と 100 は、すべての点で同じです。  
  
 FILLFACTOR 設定は、インデックスが作成または再構築されるときのみ適用されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ内の空き領域の指定された割合動的に保持しません。 表示するには、fill factor 設定を使用して、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。  
  
> [!IMPORTANT]  
>  100 未満、fillfactor の値をクラスター化インデックスを作成するため、データが占める記憶域スペースの量、影響、[!INCLUDE[ssDE](../../includes/ssde-md.md)]クラスター化インデックスを作成するときに、データを再分配します。  
  
 詳細については、「 [インデックスの FILL FACTOR の指定](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)」を参照してください。  
  
 SORT_IN_TEMPDB  **=**  {ON |**OFF** }  
 一時的な並べ替え結果を格納するかどうかを示す**tempdb**です。 既定値は OFF です。  
  
 ON  
 インデックスの構築に使用される並べ替えの中間結果が格納されている**tempdb**です。 場合、インデックスの作成に必要な時間が削減**tempdb**が別のユーザー データベースのディスク セットにします。 インデックスの構築中に使用されるディスク領域のサイズは増加します。  
  
 OFF  
 中間の並べ替え結果はインデックスと同じデータベースに格納されます。  
  
 ユーザー データベースで、インデックスを作成するために必要な容量に加えて**tempdb**について、一定の並べ替えの中間結果を格納する追加の領域がある必要があります。 詳細については、次を参照してください。[インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)です。  
  
 IGNORE_DUP_KEY **= OFF**  
 インデックスの種類が一意になることはないので、XML インデックスでは無効です。 このオプションを ON に設定すると、エラーが発生します。  
  
 DROP_EXISTING  **=**  {ON |**OFF** }  
 名前付きの、既存の XML インデックスを削除および再構築することを指定します。 既定値は OFF です。  
  
 ON  
 既存のインデックスは削除され、再構築されます。 指定するインデックス名は、現在存在するインデックスと同じにする必要がありますが、インデックス定義は変更できます。 たとえば、異なる列、並べ替え順、パーティション構成、またはインデックス オプションを指定できます。  
  
 OFF  
 指定するインデックス名が既に存在する場合、エラーが表示されます。  
  
 DROP_EXISTING を使用してインデックスの種類を変更することはできません。 また、プライマリ XML インデックスをセカンダリ XML インデックスに、またはその逆に再定義することもできません。  
  
 オンライン**= OFF**  
 インデックス操作中に、基となるテーブルとそれに関連する各インデックスに対してクエリやデータ変更を行えないことを指定します。 このバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XML インデックスに対するオンラインのインデックス構築操作はサポートされていません。 XML インデックスに対してこのオプションを ON に設定すると、エラーが発生します。 ONLINE オプションを省略するか、ONLINE を OFF に設定してください。  
  
 オフラインのインデックス操作で、XML インデックスの作成、再構築、または削除を行う場合は、テーブルで Sch-M (スキーマ修正) ロックが取得されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** |オフ}  
 行ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 インデックスにアクセスするとき、行ロックが許可されます。 いつ行ロックを使用するかは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって決定されます。  
  
 OFF  
 行ロックは使用されません。  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** |オフ}  
 ページ ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 ページにアクセスするとき、行ロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ ロックを使用する場合を決定します。  
  
 OFF  
 ページ ロックは使用されません。  
  
 MAXDOP  **=**  *max_degree_of_parallelism*  
 上書き、 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)インデックス操作の実行中の構成オプション。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
> [!IMPORTANT]  
>  MAXDOP オプションはすべての XML インデックスで構文的にサポートされていますが、プライマリ XML インデックスの場合、CREATE XML INDEX では単一のプロセッサのみが使用されます。  
  
 *max_degree_of_parallelism*を指定できます。  
  
 1  
 並列プラン生成を抑制します。  
  
 \>1  
 現在のシステム ワークロードに基づいて、並列インデックス操作で使用される最大プロセッサ数を指定の数以下に制限します。  
  
 0 (既定値)  
 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作はすべてのエディションで使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
## <a name="remarks"></a>解説  
 派生した計算列**xml**の型があるデータとしてインデックスを設定、キー列または付加非キー列、計算列のデータ型がインデックス キー列または非キー列として使用できる限り、します。 計算で、プライマリ XML インデックスを作成することはできません**xml**列です。  
  
 表示するには XML インデックスに関する情報を使用して、 [sys.xml_indexes](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)カタログ ビューです。  
  
 XML インデックスの詳細については、次を参照してください。 [XML インデックス & #40 です。SQL Server &#41;](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
## <a name="additional-remarks-on-index-creation"></a>インデックス作成に関する詳細説明  
 インデックスの作成の詳細については、「解説」セクションを参照してください。 [CREATE INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-primary-xml-index"></a>A. プライマリ XML インデックスを作成する  
 次の例では、`CatalogDescription` テーブルの `Production.ProductModel` 列にプライマリ XML インデックスを作成します。  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT * FROM sys.indexes  
            WHERE name = N'PXML_ProductModel_CatalogDescription')  
    DROP INDEX PXML_ProductModel_CatalogDescription   
        ON Production.ProductModel;  
GO  
CREATE PRIMARY XML INDEX PXML_ProductModel_CatalogDescription  
    ON Production.ProductModel (CatalogDescription);  
GO  
```  
  
### <a name="b-creating-a-secondary-xml-index"></a>B. セカンダリ XML インデックスを作成する  
 次の例では、`CatalogDescription` テーブルの `Production.ProductModel` 列にセカンダリ XML インデックスを作成します。  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.indexes  
            WHERE name = N'IXML_ProductModel_CatalogDescription_Path')  
    DROP INDEX IXML_ProductModel_CatalogDescription_Path  
        ON Production.ProductModel;  
GO  
CREATE XML INDEX IXML_ProductModel_CatalogDescription_Path   
    ON Production.ProductModel (CatalogDescription)  
    USING XML INDEX PXML_ProductModel_CatalogDescription FOR PATH ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [空間インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-index-transact-sql.md)   
 [XML インデックス &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [XML インデックス &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  


