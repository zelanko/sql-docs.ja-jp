---
title: "CREATE VIEW (Transact SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE VIEW
- VIEW_TSQL
- VIEW
- CREATE_VIEW_TSQL
- SCHEMABINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table creation [SQL Server], CREATE VIEW
- views [SQL Server], creating
- CREATE VIEW statement
- updatable partitioned views
- tables [SQL Server], virtual
- updatable views
- modifying partitioned views
- virtual tables [SQL Server]
- number of columns per view
- partitioned views [SQL Server], creating
- WITH ENCRYPTION clause
- WITH CHECK OPTION clause
- partitioned views [SQL Server], modifying
- partitioned views [SQL Server], replication
- distributed partitioned views [SQL Server]
- views [SQL Server], indexed views
- maximum number of columns per view
ms.assetid: aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 633179d7540ba4a6515c3614724a4849f40de391
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-view-transact-sql"></a>CREATE VIEW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  クエリによって内容 (列と行) が定義される仮想テーブルを作成します。 このステートメントを使用すると、データベースの 1 つまたは複数のテーブル内のデータのビューを作成できます。 たとえば、ビューは、次の目的で使用できます。  
  
-   各ユーザーのデータベースに対する認識を特化、簡素化、およびカスタマイズする。  
  
-   基になるベース テーブルに直接アクセスする権限をユーザーに与えずに、ユーザーがビューを介してデータにアクセスできるように設定することにより、セキュリティのメカニズムとして使用する。  
  
-   テーブルのスキーマが変更された場合に、そのテーブルをエミュレートするための後方互換性インターフェイスを提供する。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
CREATE [ OR ALTER ] VIEW [ schema_name . ] view_name [ (column [ ,...n ] ) ]   
[ WITH <view_attribute> [ ,...n ] ]   
AS select_statement   
[ WITH CHECK OPTION ]   
[ ; ]  
  
<view_attribute> ::=   
{  
    [ ENCRYPTION ]  
    [ SCHEMABINDING ]  
    [ VIEW_METADATA ]       
}   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE VIEW [ schema_name . ] view_name [  ( column_name [ ,...n ] ) ]   
AS <select_statement>   
[;]  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>引数
または変更  
 **適用されます**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1)。   
  
 条件付きでは既に存在する場合にのみ、ビューを変更します。 
 
 *schema_name*  
 ビューが所属するスキーマの名前を指定します。  
  
 *view_name*  
 ビューの名前を指定します。 ビュー名は、識別子の規則に従っている必要があります。 ビューの所有者名の指定は省略可能です。  
  
 *列*  
 ビューの列に付ける名前を指定します。 列名が必要なのは、算術式、関数、または定数から列を導いた場合と、名前を付けないと (通常、結合によって) 2 つ以上の列の名前が同じになる場合、および、ビュー内の列に派生元と異なる列名を付ける場合に限られます。 列名は、SELECT ステートメントで指定することもできます。  
  
 場合*列*が指定されていない、ビューの列が SELECT ステートメント内の列と同じ名前を取得します。  
  
> [!NOTE]  
>  ビューの列では、列名に対する権限は、基底となるデータのソースがどこにあるかにかかわらず、CREATE VIEW ステートメントまたは ALTER VIEW ステートメントを超えて適用されます。 たとえば、アクセス許可が与えられる場合、 **SalesOrderID** CREATE VIEW ステートメントの列で、ALTER VIEW ステートメントの名前をことができます、 **SalesOrderID** などの別の列名を持つ列**OrderRef**、ビューを使用して、関連付けられたアクセス許可も**SalesOrderID**です。  
  
 AS  
 ビューが行う動作を指定します。  
  
 *select_statement*  
 ビューを定義している SELECT ステートメントを指定します。 このステートメントでは、複数のテーブルや他のビューを使用することもできます。 作成するビューの SELECT 句で参照されるオブジェクトから選択するには、適切な権限が必要です。  
  
 ビューは、1 つの特定のテーブルの行と列の簡単なサブセットである必要はありません。 複雑な SELECT 句で、複数のテーブルまたは他のビューを使用するビューを作成することもできます。  
  
 インデックス付きビュー定義では、SELECT ステートメントは、単一のテーブル ステートメントまたは複数のテーブルの JOIN (集計は省略可) にする必要があります。  
  
 ビュー定義の SELECT 句に、次の要素を含めることはできません。  
  
-   ORDER BY 句。ただし、SELECT ステートメントの選択リストに TOP 句が同時に含まれている場合は例外です。  
  
    > [!IMPORTANT]  
    >  ORDER BY 句は、ビュー定義において TOP 句または OFFSET 句によって返される行を特定する場合にのみ使用されます。 クエリ自体にも ORDER BY を指定しない限り、ビューをクエリしたときに、ORDER BY 句で順序どおりの結果が得られるかどうかは保証されません。  
  
-   INTO キーワード。  
  
-   OPTION 句。  
  
-   一時テーブルまたはテーブル変数の参照。  
  
 *Select_statement* 、SELECT ステートメントを使用して使用することは\<join_hint > および\<table_hint > ヒントを FROM 句で指定されています。 詳細については、次を参照してください。 [FROM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/from-transact-sql.md)と[SELECT &#40;TRANSACT-SQL と #41 です。](../../t-sql/queries/select-transact-sql.md). 
  
 関数と UNION または UNION ALL で区切って複数の SELECT ステートメントで指定できます*select_statement*です。  
  
 CHECK OPTION  
 内で設定された条件に従うビューに対して実行されるすべてのデータ変更ステートメントを強制*select_statement*です。 ビューを介して行を変更する場合は、WITH CHECK OPTION を使用すると、変更がコミットされた後もビューを介して確実にデータを表示できます。  
  
> [!NOTE]  
>  ビューの基になるテーブルに対して直接更新が実行された場合は、CHECK OPTION を指定してもビューに対する確認は行われません。  
  
 ENCRYPTION  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 エントリを暗号化[sys.syscomments](../../relational-databases/system-compatibility-views/sys-syscomments-transact-sql.md) CREATE VIEW ステートメントのテキストが含まれています。 WITH ENCRYPTION を使用すると、そのビューを SQL Server レプリケーションの一部としてパブリッシュできなくなります。  
  
 SCHEMABINDING  
 基になるテーブルのスキーマにビューをバインドします。 SCHEMABINDING を指定した場合、ベース テーブルに対してビュー定義に影響を与えるような変更は行えません。 ビュー定義自体も変更または削除を変更するのには、テーブルへの依存関係を削除する最初にする必要があります。 スキーマ バインドを使用すると、 *select_statement* 2 部構成の名前を含める必要があります (*スキーマ***.***オブジェクト*) テーブル、ビュー、またはユーザー定義関数の参照されています。 参照されるオブジェクトは、すべて同じデータベース内にあることが必要です。  
  
 ビューまたはテーブル SCHEMABINDING 句を使用して作成したビューに参加することはできませんは削除しない限り、ビューが削除または変更されたため、スキーマ バインドがある不要です。 スキーマ バインドが残っている場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]からエラーが返されます。 また、ビュー定義に影響を与える ALTER TABLE ステートメントを、スキーマ バインドを持つビューに参加しているテーブルに対して実行すると、ステートメントは失敗します。  
  
 VIEW_METADATA  
 ビューを参照するクエリ用にブラウズ モード メタデータが要求されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、DB-Library、ODBC、および OLE DB API に対して、ベース テーブルではなくビューに関するメタデータ情報を返します。 ブラウズ モード メタデータは追加のメタデータをインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]これらのクライアント側 Api に返されます。 クライアント側 API ではこのメタデータによって、更新可能なクライアント側カーソルを実装できます。 ブラウズ モード メタデータには、結果セット内の列が属するベース テーブルの情報が含まれています。  
  
 VIEW_METADATA で作成したビューの場合、ブラウズ モード メタデータでは結果セット内のビューの列の説明で、ベース テーブル名ではなくビュー名が返されます。  
  
 WITH VIEW_METADATA をすべての列を使用して、ビューを作成する場合を除く、**タイムスタンプ**列にいる場合、ビューに INSTEAD OF INSERT または INSTEAD OF UPDATE トリガーします。 更新可能なビューの詳細については、「解説」を参照してください。  
  
## <a name="remarks"></a>解説  
 ビューは現在のデータベースでのみ作成できます。 CREATE VIEW は、クエリ バッチの最初のステートメントであることが必要です。 1 つのビューで保持できる列の数は最大 1,024 です。  
  
 ビューからクエリを実行するときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ステートメント内の任意の場所参照されているすべてのデータベース オブジェクトが存在して、ステートメントのコンテキストで有効であるし、データ変更ステートメントには、すべてのデータが違反していないことを確認するためのチェック整合性の規則。 確認に失敗すると、エラー メッセージが返されます。 確認に成功すると、指定した動作が、基になるテーブルに対する動作に変換されます。  
  
 テーブルまたはビューを削除、ビューが依存している場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ビューの使用が試行されたときに、エラー メッセージを生成します。 テーブルの構造が以前のベース テーブルから変わっていなければ、削除されたテーブルやビューの代わりになる、新しいテーブルまたはビューを作成すると、ビューは再び使用可能になります。 新しいテーブルまたはビューの構造が変化した場合は、ビューを削除し、再作成する必要があります。  
  
 ビューが SCHEMABINDING 句を使用して作成されていない場合[sp_refreshview](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)ビューの定義に影響を与える、ビューを基になるオブジェクトが変更されたときに実行する必要があります。 この操作を行わないと、ビューのクエリ時に、予期しない結果が表示される可能性があります。  
  
 次のカタログ ビューでビューに関する情報が格納されているビューが作成されると、: [sys.views](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)、 [sys.columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)、および[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)です。 CREATE VIEW ステートメントのテキストが格納されている、 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビューです。  
  
 定義されたビューのインデックスを使用するクエリ**数値**または**float**式は、ビューのインデックスを使用しない同様のクエリとは異なる結果を持つ可能性があります。 この相違は、基になるテーブルに対して INSERT、DELETE、または UPDATE 操作を行った場合の丸め誤差によって発生することがあります。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ビューが作成されるときに、SET QUOTED_IDENTIFIER と SET ANSI_NULLS の設定を保存します。 これらの元の設定は、ビューの使用時に、ビューの解析で使用されます。 したがって、ビューへアクセスするとき、SET QUOTED_IDENTIFIER と SET ANSI_NULLS のクライアント セッションの設定によってビュー定義に影響が生じることはありません。  
  
## <a name="updatable-views"></a>更新可能なビュー  
 次の条件を満たす場合、ビューから基になるデータベース テーブルのデータを変更できます。  
  
-   UPDATE、INSERT、DELETE ステートメントなどの変更で、1 つのベース テーブルのみの列を参照している。  
  
-   ビューで変更される列は、テーブルの列の基になるデータを直接参照する必要があります。 ただし次のような方法では、列は派生されません。  
  
    -   集計関数 (AVG、COUNT、SUM、MIN、MAX、GROUPING、STDEV、STDEVP、VAR、および VARP)。  
  
    -   計算。 他の列を使用する式を基にして列を計算することはできません。 計算に相当する set 演算子 UNION、UNION ALL、CROSSJOIN、EXCEPT、INTERSECT を使用して形成される列も計算されません。  
  
-   変更される列が、GROUP BY、HAVING、または DISTINCT 句の影響を受けない。  
  
-   TOP がで使用されない任意の場所、 *select_statement*の WITH CHECK OPTION 句と共に表示します。  
  
 以前の制限は、ビュー自体に適用されるのと同様に、ビューの FROM 句のサブクエリにも適用されます。 通常は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、ビュー定義からベース テーブルへの変更を正確にトレースできる必要があります。 詳細については、次を参照してください。[変更データ ビューを経由した](../../relational-databases/views/modify-data-through-a-view.md)です。  
  
 以前の制約によってビューから直接データを変更できない場合は、次の方法を試してください。  
  
-   **Instead of トリガー**  
  
     ビューに INSTEAD OF トリガーを作成して、そのビューを更新可能にできます。 INSTEAD OF トリガーは、そのトリガーが定義されているデータ変更ステートメントの代わりに実行されます。 このトリガーで、データ変更ステートメントを処理する一連の操作を指定できます。 したがって、特定のデータ変更ステートメント (INSERT、UPDATE、または DELETE) に対する INSTEAD OF トリガーがビューに存在する場合は、そのステートメントを介して対応するビューを更新できます。 INSTEAD of トリガーの詳細については、次を参照してください。 [DML トリガー](../../relational-databases/triggers/dml-triggers.md)です。  
  
-   **パーティション ビュー**  
  
     ビューがパーティション ビューである場合は、いくつかの制限の範囲内で更新可能です。 必要に応じて、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、ローカル パーティション ビュー (参加しているすべてのテーブルとビューが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にあるビュー) と分散パーティション ビュー (ビュー内の少なくとも 1 つのテーブルが別のサーバーまたはリモート サーバー上にあるビュー) が区別されます。  
  
## <a name="partitioned-views"></a>パーティション ビュー  
 パーティション ビューは、同じ構造のメンバー テーブルの UNION ALL によって定義されるビューです。ただし、これらのメンバー テーブルは、同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内、または連合データベース サーバーと呼ばれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバー インスタンスの独立したグループ内に、複数のテーブルとして個別に格納されます。  
  
> [!NOTE]  
>  1 台のサーバーに対してローカルでデータをパーティション分割する方法としては、パーティション テーブルをお勧めします。 詳細については、「 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。  
  
 パーティション分割構成の設計時には、各パーティションに所属するデータを明確にする必要があります。 データなど、`Customers`テーブルは、次の 3 つのサーバーの場所で次の 3 つのメンバー テーブルで配布:`Customers_33`で`Server1`、`Customers_66`で`Server2`と`Customers_99`で`Server3`です。  
  
 パーティション ビュー`Server1`次のように定義します。  
  
```  
--Partitioned view as defined on Server1  
CREATE VIEW Customers  
AS  
--Select from local member table.  
SELECT *  
FROM CompanyData.dbo.Customers_33  
UNION ALL  
--Select from member table on Server2.  
SELECT *  
FROM Server2.CompanyData.dbo.Customers_66  
UNION ALL  
--Select from mmeber table on Server3.  
SELECT *  
FROM Server3.CompanyData.dbo.Customers_99;  
```  
  
 一般に、次の形式のビューをパーティション ビューといいます。  
  
```  
SELECT <select_list1>  
FROM T1  
UNION ALL  
SELECT <select_list2>  
FROM T2  
UNION ALL  
...  
SELECT <select_listn>  
FROM Tn;  
```  
  
## <a name="conditions-for-creating-partitioned-views"></a>パーティション ビューを作成する条件  
  
1.  選択リスト (`list`  
  
    -   メンバー テーブルのすべての列は、ビュー定義の列リストで選択する必要があります。  
  
    -   それぞれの `select list` の同じ位置にある列は、照合順序も含めて同じ型であることが必要です。 列が暗黙的に変換される型であるという条件だけでは十分ではありません。これは UNION の場合とは異なります。  
  
         また、少なくとも 1 つの列 (たとえば`<col>`) の同じ序数位置でのすべての選択リストに表示する必要があります。 これは、`<col>`方法で定義する必要がありますをメンバー テーブル`T1, ..., Tn`CHECK 制約がある`C1, ..., Cn`で定義されている`<col>`、それぞれします。  
  
         テーブル `C1` の制約 `T1` は、次の形式で定義する必要があります。  
  
        ```  
        C1 ::= < simple_interval > [ OR < simple_interval > OR ...]  
        < simple_interval > :: =   
        < col > { < | > | \<= | >= | = < value >}   
        | < col > BETWEEN < value1 > AND < value2 >  
        | < col > IN ( value_list )  
        | < col > { > | >= } < value1 > AND  
        < col > { < | <= } < value2 >  
        ```  
  
    -   これらの制約は、`<col>` に指定したすべての値が `C1, ..., Cn` の制約の 1 つにのみ該当するような形式にする必要があります。つまり、連続せずかつ重複しない間隔を持つ制約セットを形成するように定義します。 連続しない制約が定義されている列 `<col>` は、パーティション分割列と呼ばれます。 パーティション分割列は、基になるテーブルではそれぞれ異なる名前が付いている場合があります。 前に示したパーティション分割列の条件を満たすには、パーティション分割列に対して制約が有効かつ信頼されている必要があります。 制約が無効にした場合は、制約、CHECK 制約を使用して、チェック再度有効に*constraint_name* ALTER TABLE、およびそれらを検証する WITH CHECK オプションを使用するオプションです。  
  
         次は、有効な制約のセットの例です。  
  
        ```  
        { [col < 10], [col between 11 and 20] , [col > 20] }  
        { [col between 11 and 20], [col between 21 and 30], [col between 31 and 100] }  
        ```  
  
    -   選択リストで同じ列を複数回使用することはできません。  
  
2.  パーティション分割列  
  
    -   パーティション分割列は、テーブルの PRIMARY KEY の一部です。  
  
    -   計算列、id、既定では指定できませんまたは**タイムスタンプ**列です。  
  
    -   メンバー テーブルの 1 つの列に複数の制約が定義されている場合、データベース エンジンではすべての制約が無視され、ビューがパーティション ビューであるかどうかを判断する際にそれらの制約は考慮されません。 パーティション ビューの条件を満たすには、パーティション分割列にパーティション分割制約を 1 つだけ定義する必要があります。  
  
    -   パーティション分割列の更新可能性に制限はありません。  
  
3.  メンバー テーブルまたは基になるテーブル `T1, ..., Tn`  
  
    -   テーブルには、ローカル テーブルまたはを実行している他のコンピューターからテーブルを指定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]による 4 部構成の名前、または、OPENDATASOURCE ベースまたは OPENROWSET ベースの名前で参照されています。 OPENDATASOURCE および OPENROWSET の構文では、テーブル名は指定できますが、パススルー クエリは指定できません。 詳細については、次を参照してください。 [OPENDATASOURCE (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/opendatasource-transact-sql.md)と[OPENROWSET &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/openrowset-transact-sql.md).  
  
         1 つ以上のメンバー テーブルがリモートにある場合、そのビューは分散パーティション ビューと呼ばれ、さらに条件が適用されます。 これらの条件については後で説明します。  
  
    -   UNION ALL ステートメントで組み合わせるテーブルのセットに、同じテーブルを 2 回指定することはできません。  
  
    -   メンバー テーブルでは、テーブル内の計算列上にインデックスを作成することはできません。  
  
    -   メンバー テーブルでは、すべての PRIMARY KEY 制約が同じ数の列に対して定義されている必要があります。  
  
    -   ビューのすべてのメンバー テーブルには、同じ ANSI PADDING 設定を指定する必要があります。 これは、いずれかを使用して設定できます、**ユーザー オプション**オプション**sp_configure**または SET ステートメント。  
  
## <a name="conditions-for-modifying-data-in-partitioned-views"></a>パーティション ビューのデータを変更する条件  
 パーティション ビューのデータを変更するステートメントには、次の制限が適用されます。  
  
-   INSERT ステートメントでは、基になるメンバー テーブルで列に DEFAULT 制約が定義されているか NULL 値が許容されている場合でも、ビューのすべての列に値を提供する必要があります。 メンバー テーブルの列に DEFAULT 定義がある場合、ステートメントではこれらの列に DEFAULT キーワードを使用できません。  
  
-   パーティション分割列に挿入する値は、基になる制約の少なくとも 1 つを満たしている必要があります。満たしていない場合、INSERT 操作は制約違反で失敗します。  
  
-   UPDATE ステートメントでは、対応するメンバー テーブルで列の DEFAULT 値が定義されている場合でも、SET 句の値として DEFAULT キーワードを指定することはできません。  
  
-   ビューの列が、1 つ以上のメンバー テーブルで ID 列になっている場合、INSERT ステートメントまたは UPDATE ステートメントでこの列を変更することはできません。  
  
-   メンバー テーブルの 1 つ含まれている場合、**タイムスタンプ**列で、INSERT または UPDATE ステートメントを使用してデータを変更することはできません。  
  
-   メンバー テーブルに、トリガー、ON UPDATE CASCADE/SET NULL/SET DEFAULT 制約、または ON DELETE CASCADE/SET NULL/SET DEFAULT 制約が含まれている場合、ビューを変更することはできません。  
  
-   ステートメント内に、同じビューまたはいずれかのメンバー テーブルとの自己結合が指定された場合、パーティション ビューに対して INSERT、UPDATE、および DELETE 操作は許可されません。  
  
-   サポートされていないデータの一括インポート パーティション分割されたビュー **bcp**または BULK INSERT および INSERT.SELECT * FROM OPENROWSET(BULK...) ステートメントを使用してデータを一括インポートする場合のフォーマット ファイルの使用方法を示します。 ただし、行を挿入できます複数パーティション分割されたビューを使用して、[挿入](../../t-sql/statements/insert-transact-sql.md)ステートメントです。  
  
    > [!NOTE]  
    >  パーティション ビューを更新するには、メンバー テーブルに対して INSERT、UPDATE、DELETE の各権限を持っている必要があります。  
  
## <a name="additional-conditions-for-distributed-partitioned-views"></a>分散パーティション ビューの追加条件  
 分散パーティション ビュー (1 つ以上のメンバー テーブルがリモートの場合) では、次の追加条件が適用されます。  
  
-   更新によって影響を受けるすべてのノードにおいて原子性を保証するため、分散トランザクションが起動されます。  
  
-   INSERT、UPDATE、または DELETE ステートメントが動作するには、XACT_ABORT SET オプションを ON に設定する必要があります。  
  
-   型のリモート テーブル内の列**smallmoney**はパーティション ビューで参照されるとしてマップ**money**です。 そのため、ローカル テーブルの対応する列 (選択リスト内の同じ序数位置) では、型でなければなりませんも**money**です。  
  
-   データベース互換性レベル 110 以降では、型のリモート テーブル内の列**smalldatetime**はパーティション ビューで参照されるとしてマップ**smalldatetime**です。 対応する列 (選択リスト内の同じ序数位置)、ローカル テーブルである必要があります**smalldatetime**です。 これは、以前のバージョンからの動作の変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型のリモート テーブルで列の**smalldatetime**はパーティション ビューで参照されるとしてマップ**datetime**とローカル テーブルの対応する列は、型でなければなりません**datetime**です。 詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  
  
-   パーティション ビューのリンク サーバーは、ループバック リンク サーバーとして使用できません。 ループバック リンク サーバーは、同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指すリンク サーバーです。  
  
 更新可能なパーティション ビューとリモート テーブルに関連する INSERT、UPDATE、DELETE 操作では、SET ROWCOUNT オプションの設定は無視されます。  
  
 メンバー テーブルとビュー定義が準備されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のクエリ オプティマイザーでは、クエリを効率的に使用してメンバー テーブルからデータにアクセスする高度なプランが構築されます。 クエリ プロセッサでは、CHECK 制約の定義を使用して、キー値の分布が複数のメンバー テーブルにマップされます。 ユーザーがクエリを実行すると、クエリ プロセッサでは、マップと WHERE 句で指定した値とが比較され、メンバー サーバー間のデータ転送が最も少なくなる実行プランが構築されます。 したがって、いくつかのメンバー テーブルがリモート サーバー上にある場合でも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスでは転送の対象となる分散データの量が最も少なくなる方法で分散クエリが解決されます。  
  
## <a name="considerations-for-replication"></a>レプリケーションに関する注意点  
 レプリケーションに関係するメンバー テーブルのパーティション ビューを作成するには、次の点に注意してください。  
  
-   基になるテーブルがマージ レプリケーションや、更新サブスクリプションを使用するトランザクション レプリケーションに関係している場合、 **uniqueidentifier**列は、選択リストにも含まれる必要があります。  
  
     パーティション分割されたビューに対する INSERT 操作は、NEWID() 値を指定する必要があります、 **uniqueidentifier**列です。 に対する UPDATE 操作、 **uniqueidentifier**列は、DEFAULT キーワードを使用できないために、値としての NEWID() を入力する必要があります。  
  
-   ビューを使用した更新のレプリケーションは、2 つの異なるデータベースでのテーブルのレプリケーションと同じです。つまり、テーブルは異なるレプリケーション エージェントで管理されるため、更新の順序は保証されません。  
  
## <a name="permissions"></a>Permissions  
 データベースの CREATE VIEW 権限と、ビューが作成されているスキーマの ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  

次の例では、AdventureWorks 2012 または AdventureWorksDW データベースを使用します。  

### <a name="a-using-a-simple-create-view"></a>A. 単純な CREATE VIEW を使用する  
 次の例では、ビューを作成して、単純な`SELECT`ステートメントです。 単純なビューは、列の組み合わせを頻繁にクエリする場合に便利です。 このビューのデータは、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの `HumanResources.Employee` テーブルと `Person.Person` テーブルから取得されます。 データの従業員の名前と採用の日付情報を提供する[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]です。 従業員の勤続祝いの担当者用にビューを作成することができますが、この担当者はテーブルのすべてのデータにアクセスできるわけではありません。  
  
```  
CREATE VIEW hiredate_view  
AS   
SELECT p.FirstName, p.LastName, e.BusinessEntityID, e.HireDate  
FROM HumanResources.Employee e   
JOIN Person.Person AS p ON e.BusinessEntityID = p.BusinessEntityID ;  
GO  
  
```  
  
### <a name="b-using-with-encryption"></a>B. 暗号化を使用する  
 次の例では、`WITH ENCRYPTION`オプションを選択し、計算列、名前が変更された列、および複数の列を示しています。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
```  
CREATE VIEW Purchasing.PurchaseOrderReject  
WITH ENCRYPTION  
AS  
SELECT PurchaseOrderID, ReceivedQty, RejectedQty,   
    RejectedQty / ReceivedQty AS RejectRatio, DueDate  
FROM Purchasing.PurchaseOrderDetail  
WHERE RejectedQty / ReceivedQty > 0  
AND DueDate > CONVERT(DATETIME,'20010630',101) ;  
GO  
  
```  
  
### <a name="c-using-with-check-option"></a>C. WITH CHECK OPTION を使用する  
 次の例は、という名前のビューを示しています。`SeattleOnly`を 5 つのテーブルを参照でき、データの変更をシアトルに住んでいる従業員だけに適用します。  
  
```  
CREATE VIEW dbo.SeattleOnly  
AS  
SELECT p.LastName, p.FirstName, e.JobTitle, a.City, sp.StateProvinceCode  
FROM HumanResources.Employee e  
INNER JOIN Person.Person p  
ON p.BusinessEntityID = e.BusinessEntityID  
    INNER JOIN Person.BusinessEntityAddress bea   
    ON bea.BusinessEntityID = e.BusinessEntityID   
    INNER JOIN Person.Address a   
    ON a.AddressID = bea.AddressID  
    INNER JOIN Person.StateProvince sp   
    ON sp.StateProvinceID = a.StateProvinceID  
WHERE a.City = 'Seattle'  
WITH CHECK OPTION ;  
GO  
```  
  
### <a name="d-using-built-in-functions-within-a-view"></a>D. ビュー内部の組み込み関数を使用する  
 次の例では、組み込み関数を含むビュー定義を示しています。 関数を使用するときには、派生列に列名を指定する必要があります。  
  
```  
CREATE VIEW Sales.SalesPersonPerform  
AS  
SELECT TOP (100) SalesPersonID, SUM(TotalDue) AS TotalSales  
FROM Sales.SalesOrderHeader  
WHERE OrderDate > CONVERT(DATETIME,'20001231',101)  
GROUP BY SalesPersonID;  
GO  

```  
  
### <a name="e-using-partitioned-data"></a>E. パーティション分割されたデータを使用する  
 次の例では、という名前のテーブル`SUPPLY1`、 `SUPPLY2`、 `SUPPLY3`、および`SUPPLY4`です。 これらのテーブルは、異なる国や地域にある 4 か所のオフィスの仕入れ先テーブルに対応しています。  
  
```  
--Create the tables and insert the values.  
CREATE TABLE dbo.SUPPLY1 (  
supplyID INT PRIMARY KEY CHECK (supplyID BETWEEN 1 and 150),  
supplier CHAR(50)  
);  
CREATE TABLE dbo.SUPPLY2 (  
supplyID INT PRIMARY KEY CHECK (supplyID BETWEEN 151 and 300),  
supplier CHAR(50)  
);  
CREATE TABLE dbo.SUPPLY3 (  
supplyID INT PRIMARY KEY CHECK (supplyID BETWEEN 301 and 450),  
supplier CHAR(50)  
);  
CREATE TABLE dbo.SUPPLY4 (  
supplyID INT PRIMARY KEY CHECK (supplyID BETWEEN 451 and 600),  
supplier CHAR(50)  
);  
GO  
INSERT dbo.SUPPLY1 VALUES ('1', 'CaliforniaCorp'), ('5', 'BraziliaLtd')  
, ('231', 'FarEast'), ('280', 'NZ')  
, ('321', 'EuroGroup'), ('442', 'UKArchip')  
, ('475', 'India'), ('521', 'Afrique');  
GO  
--Create the view that combines all supplier tables.  
CREATE VIEW dbo.all_supplier_view  
WITH SCHEMABINDING  
AS  
SELECT supplyID, supplier  
  FROM dbo.SUPPLY1  
UNION ALL  
SELECT supplyID, supplier  
  FROM dbo.SUPPLY2  
UNION ALL  
SELECT supplyID, supplier  
  FROM dbo.SUPPLY3  
UNION ALL  
SELECT supplyID, supplier  
  FROM dbo.SUPPLY4;  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-creating-a-simple-view"></a>F. 単純なビューを作成します。  
 次の例では、ソース テーブルから一部の列のみを選択して、ビューを作成します。  
  
```  
CREATE VIEW DimEmployeeBirthDates AS  
SELECT FirstName, LastName, BirthDate   
FROM DimEmployee;  
```  
  
### <a name="g-create-a-view-by-joining-two-tables"></a>G. 2 つのテーブルを結合することで、ビューを作成します。  
 次の例を使用して、ビューを作成する、`SELECT`ステートメントを`OUTER JOIN`です。 結合クエリの結果は、ビューを設定します。  
  
```  
CREATE VIEW view1  
AS 
SELECT fis.CustomerKey, fis.ProductKey, fis.OrderDateKey, 
  fis.SalesTerritoryKey, dst.SalesTerritoryRegion  
FROM FactInternetSales AS fis   
LEFT OUTER JOIN DimSalesTerritory AS dst   
ON (fis.SalesTerritoryKey=dst.SalesTerritoryKey);  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/alter-view-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [DROP VIEW &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-view-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [ストアド プロシージャの作成](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_refreshview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sys.views &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

