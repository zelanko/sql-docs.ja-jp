---
title: "sp_describe_undeclared_parameters (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_describe_undeclared_parameters
- sp_describe_undeclared_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_undeclared_parameters
ms.assetid: 6f016da6-dfee-4228-8b0d-7cd8e7d5a354
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bae5aebe0afe1861251628bd0eb447ab97b226dd
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdescribeundeclaredparameters-transact-sql"></a>sp_describe_undeclared_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  宣言されていないパラメーターに関するメタデータを含む結果セットを返す、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 使用されている各パラメーターの検討、  **@tsql** バッチで宣言されていないが、  **@params**です。 これらの各パラメーターに対して 1 行のデータを含む結果セットが返されます。そのパラメーターについて推論される型の情報も含まれます。 このプロシージャには空の結果セットが返されます、  **@tsql** 入力バッチで宣言されている以外のパラメーターを持たない **@params**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_describe_undeclared_parameters   
    [ @tsql = ] 'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' data type ] [, ...n]  
```  
  
## <a name="arguments"></a>引数  
 [  **@tsql =** ] **'***Transact SQL_batch***'**  
 1 つまたは複数[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 *Transact SQL_batch*あります**nvarchar (***n***)**または**nvarchar (max)**です。  
  
 [  **@params =** ] **N'***パラメーター***'**  
 @paramsパラメーターの宣言文字列の提供、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、sp_executesql と同様に動作します。 *パラメーター*あります**nvarchar (***n***)**または**nvarchar (max)**です。  
  
 1 つの文字列に埋め込まれたすべてのパラメーターの定義を含む*Transact SQL_batch*です。 この文字列は Unicode 定数または Unicode 変数にする必要があります。 各パラメーター定義は、パラメーター名とデータ型で構成されます。 n は、追加のパラメーター定義を示すプレースホルダーです。 TRANSACT-SQL ステートメントまたはステートメント内のバッチにパラメーターが含まれない場合@paramsは必要ありません。 このパラメーターの既定値は NULL です。  
  
 データ型  
 パラメーターのデータ型です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **sp_describe_undeclared_parameters**常に返します 0 のリターン ステータスに成功します。 プロシージャがエラーをスローすると、プロシージャが RPC として呼び出された、sys.dm_exec_describe_first_result_set の error_type 列」の説明に従って、エラーの種類で戻り値の状態が設定されます。 プロシージャが呼び出されると[!INCLUDE[tsql](../../includes/tsql-md.md)]、戻り値は 0、エラーの場合であっても、常にします。  
  
## <a name="result-sets"></a>結果セット  
 **sp_describe_undeclared_parameters**次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int NOT NULL**|結果セット内のパラメーターの位置を示す序数を格納します。 最初のパラメーターの位置は 1 で指定されます。|  
|**name**|**sysname は NOT NULL**|パラメーターの名前を格納します。|  
|**suggested_system_type_id**|**int NOT NULL**|含まれています、 **system_type_id** sys.types で指定されたパラメーターのデータ型。<br /><br /> CLR 型の場合でも、 **system_type_name**列は NULL を返しますが、この列は値 240 を返します。|  
|**suggested_system_type_name**|**nvarchar (256) NULL**|データ型の名前を格納します。 パラメーターのデータ型に指定されている引数 (長さ、有効桁数、小数点以下桁数など) を含みます。 データ型がユーザー定義の別名型の場合は、基になるシステム型がここで指定されます。 CLR ユーザー定義データ型である場合は、この列に NULL が返されます。 パラメーターの型を推論できない場合は、NULL が返されます。|  
|**suggested_max_length**|**smallint NOT NULL**|Sys.columns を参照してください。 **max_length**列の説明。|  
|**suggested_precision**|**tinyint NOT NULL**|Sys.columns を参照してください。 有効桁数の列の説明。|  
|**suggested_scale**|**tinyint NOT NULL**|Sys.columns を参照してください。 スケールの列の説明。|  
|**suggested_user_type_id**|**int NULL**|CLR 型と別名型の場合、sys.types で指定された列のデータ型の user_type_id を格納します。 それ以外の場合は NULL です。|  
|**suggested_user_type_database**|**sysname NULL**|CLR 型と別名型の場合、その型が定義されたデータベースの名前を格納します。 それ以外の場合は NULL です。|  
|**suggested_user_type_schema**|**sysname NULL**|CLR 型と別名型の場合、その型が定義されたスキーマの名前を格納します。 それ以外の場合は NULL です。|  
|**suggested_user_type_name**|**sysname NULL**|CLR 型と別名型の場合、その型の名前を格納します。 それ以外の場合は NULL です。|  
|**suggested_assembly_qualified_type_name**|**nvarchar (4000) NULL**|CLR 型の場合は、アセンブリと型を定義するクラスの名前を返します。 それ以外の場合は NULL です。|  
|**suggested_xml_collection_id**|**int NULL**|Sys.columns で指定されたパラメーターのデータ型の xml_collection_id を格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_xml_collection_database**|**sysname NULL**|この型に関連付けられている XML スキーマ コレクションが定義されているデータベースを格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_xml_collection_schema**|**sysname NULL**|この型に関連付けられている XML スキーマ コレクションが定義されているスキーマを格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_xml_collection_name**|**sysname NULL**|この型に関連付けられている XML スキーマ コレクションの名前を格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_is_xml_document**|**ビット NOT NULL**|返される型が XML とその型が XML ドキュメントであることを保証する場合は、1 を返します。 それ以外の場合は 0 を返します。|  
|**suggested_is_case_sensitive**|**ビット NOT NULL**|列がない場合に区別して文字列型と 0 の場合は、1 を返します。|  
|**suggested_is_fixed_length_clr_type**|**ビット NOT NULL**|この列が固定長の CLR 型の場合は 1、それ以外の場合は 0 を返します。|  
|**suggested_is_input**|**ビット NOT NULL**|パラメーターが、代入の左辺以外の場所で使用される場合は 1 を返します。 それ以外の場合は 0 を返します。|  
|**suggested_is_output**|**ビット NOT NULL**|パラメーターが代入の左辺で使用される場合、またはストアド プロシージャの出力パラメーターに渡される場合は 1 を返します。 それ以外の場合は 0 を返します。|  
|**formal_parameter_name**|**sysname NULL**|パラメーターがストアド プロシージャまたはユーザー定義関数の引数の場合は、対応する仮パラメーターの名前を返します。 それ以外の場合は NULL を返します。|  
|**suggested_tds_type_id**|**int NOT NULL**|内部使用です。|  
|**suggested_tds_length**|**int NOT NULL**|内部使用です。|  
  
## <a name="remarks"></a>解説  
 **sp_describe_undeclared_parameters**を返しますが常にステータス 0 を返します。  
  
 最も一般的な使用方法は、パラメーターを含み、それらのパラメーターを任意の方法で処理する必要がある [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがアプリケーションで指定される場合です。 例はなどのユーザー インターフェイス (ODBCTest または rowsetviewer など)、ユーザーが ODBC パラメーターの構文を使用してクエリを提供します。 このような場合、アプリケーションは動的にパラメーターの数を検出し、それぞれのパラメーターに対してユーザーに入力を求める必要があります。  
  
 別の例として、ユーザー入力なしで、アプリケーションがパラメーターをループして、そのデータを他の場所 (テーブルなど) から取得する必要がある場合が挙げられます。 この場合は、アプリケーションはすべてのパラメーター情報を一度に渡す必要はありません。 代わりに、アプリケーションはプロバイダーからすべてのパラメーター情報を取得し、データ自体はテーブルから取得することができます。 使用したコード**sp_describe_undeclared_parameters**はより汎用的可能性が低い場合は、データが変更を後で構造の変更が必要です。  
  
 **sp_describe_undeclared_parameters**ケースの次のいずれかでエラーが返されます。  
  
-   場合、入力@tsqlが無効です[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 有効性は、解析および分析によって決まりますが、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 決定する際に、クエリの最適化中または実行中に、バッチによるエラーが考慮されないかどうか、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチが無効です。  
  
-   場合@paramsが NULL でない文字列を保持するが、パラメーターの宣言の構文が有効な文字列ではないか、2 回以上のパラメーターを宣言する文字列が含まれている場合。  
  
-   場合、入力[!INCLUDE[tsql](../../includes/tsql-md.md)]パラメーターで宣言されているバッチが、同じ名前のローカル変数を宣言@paramsです。  
  
-   ステートメントによって一時テーブルが作成される場合。  
  
 場合@tsqlで宣言されている以外のパラメーターを持たない@paramsプロシージャは、空の結果セットを返します。  
  
## <a name="parameter-selection-algorithm"></a>パラメーター選択アルゴリズム  
 宣言されていないパラメーターを持つクエリの場合、宣言されていないパラメーターのデータ型の推論は 3 つの手順で実行されます。  
  
 **手順 1**  
  
 宣言されていないパラメーターを持つクエリのデータ型の推論の最初の手順は、宣言されていないパラメーターに依存しないデータ型を持つすべてのサブ式のデータ型を見つけることです。 型は次の式に対して特定できます。  
  
-   列、定数、変数、および宣言されたパラメーター。  
  
-   ユーザー定義関数 (UDF) の呼び出しの結果。  
  
-   すべての入力について、宣言されていないパラメーターに依存しないデータ型を持つ式。  
  
 たとえば、クエリ`SELECT dbo.tbl(@p1) + c1 FROM t1 WHERE c2 = @p2 + 2`です。 式 dbo.tbl (@p1) + c1 と c2 があるデータ型、および式@p1と@p2+ 2 がありません。  
  
 この手順の実行後、UDF の呼び出し以外の任意の式に、データ型のない 2 つの引数が含まれている場合、型推論はエラーで失敗します。 たとえば、次のすべての式ではエラーが発生します。  
  
```  
SELECT * FROM t1 WHERE @p1 = @p2  
SELECT * FROM t1 WHERE c1 = @p1 + @p2  
SELECT * FROM t1 WHERE @p1 = SUBSTRING(@p2, 2, 3)  
```  
  
 次の例ではエラーは発生しません。  
  
```  
SELECT * FROM t1 WHERE @p1 = dbo.tbl(c1, @p2, @p3)  
```  
  
 **手順 2**  
  
 指定された宣言されていないパラメーターの@p、型推論アルゴリズムは、最も内側の式 E を検索 (@p) を格納している@pは、次のいずれか。  
  
-   比較演算子または代入演算子の引数。  
  
-   ユーザー定義関数 (テーブル値 UDF を含む)、プロシージャ、またはメソッドの引数。  
  
-   引数、**値**の句、**挿入**ステートメントです。  
  
-   引数、**キャスト**または**変換**です。  
  
 型推論アルゴリズムは検索対象のデータ型 TT (@p) e (@p)。 前の例の場合、対象のデータ型は以下のとおりです。  
  
-   比較または代入の反対側のデータ型。  
  
-   この引数が渡されるパラメーターの宣言されたデータ型。  
  
-   この値が挿入される列のデータ型。  
  
-   このステートメントがキャストまたは変換するデータ型。  
  
 たとえば、クエリ`SELECT * FROM t WHERE @p1 = dbo.tbl(@p2 + c1)`です。 E (@p1) = @p1、E (@p2) = @p2 + c1、TT (@p1) TT dbo.tbl の宣言された戻り値のデータ型は、(@p2) は dbo.tbl の宣言されたパラメーター データ型です。  
  
 場合@p型推論アルゴリズムを決定、手順 2. の冒頭に記載されている任意の式に含まれていない E (@p) は、最大のスカラー式を含む@p、型推論アルゴリズムは、計算対象のデータ型 TT (@p) e (@p)。 たとえば、クエリが SELECT `@p + 2` 、E (@p) = @p + 2、TT はありません (@p)。  
  
 **手順 3**  
  
 E ようになりました (@p) と TT (@p) は、識別された、型推論アルゴリズムは、データ型を@p次の 2 つの方法のいずれかで。  
  
-   単純な推論  
  
     場合 E (@p) =@pおよび TT (@p) が存在する、つまり場合、@pが直接、手順 2.、型推論アルゴリズムの冒頭に記載されている式のいずれかの引数には、データ型があると推測@pTT (にする@p). 例:  
  
    ```  
    SELECT * FROM t WHERE c1 = @p1 AND @p2 = dbo.tbl(@p3)  
    ```  
  
     データ型を@p1、 @p2、および@p3c1 のデータ型、dbo.tbl の戻り値のデータ型 dbo.tbl のパラメーターのデータ型をそれぞれになります。  
  
     特殊なケースとして場合@pに渡す引数は、 \<、>、 \<=、または > = 演算子、単純な推論のルールは適用されません。 型推論アルゴリズムは、次のセクションで説明する一般的な推論のルールを使用します。 たとえば、c1 がデータ型 char(30) の列である場合に、以下の 2 つのクエリについて考えてみます。  
  
    ```  
    SELECT * FROM t WHERE c1 = @p  
    SELECT * FROM t WHERE c1 > @p  
    ```  
  
     最初のケースで、型推論アルゴリズムは**char (30)**のデータ型として@pこのトピックの前半の規則に従ってします。 2 番目のケースで、型推論アルゴリズムは**varchar (8000)**次のセクションで、一般的な推論の規則に従ってします。  
  
-   一般的な推論  
  
     単純な推論が適用されない場合、次のデータ型は宣言されていないパラメーターと見なされます。  
  
    -   整数データ型 (**ビット**、 **tinyint**、 **smallint**、 **int**、 **bigint**)  
  
    -   Money データ型 (**smallmoney**、 **money**)  
  
    -   浮動小数点データ型 (**float**、**実際**)  
  
    -   **numeric (38, 19)** -その他の numeric または decimal データ型は考慮されません。  
  
    -   **varchar (8000)**、 **varchar (max)**、 **nvarchar (4000)**、および**nvarchar (max)** - その他の文字列データ型 (など**テキスト**、 **char (8000)**、 **nvarchar (30)**など) は考慮されません。  
  
    -   **varbinary (8000)**と**varbinary (max)** -その他のバイナリ データ型は考慮されません (など**イメージ**、 **binary (8000)**、 **varbinary (30)**, などです。)。  
  
    -   **日付**、 **time (7)**、 **smalldatetime**、 **datetime**、 **datetime2 (7)**、 **datetimeoffset (7)** - その他の日付し、時刻型のように**time(4)**とは見なされません。  
  
    -   **sql_variant**  
  
    -   **xml**  
  
    -   CLR システム定義型 (**hierarchyid**、 **geometry**、 **geography**)  
  
    -   CLR ユーザー定義型  
  
### <a name="selection-criteria"></a>選択基準  
 候補のデータ型のうち、クエリを無効にするデータ型は拒否されます。 候補の残りのデータ型から、型推論アルゴリズムが次のルールに従って 1 つを選択します。  
  
1.  電子メールで暗黙的な変換の最小数を生成するデータ型 (@p) を選択します。 特定のデータ型が、電子メールのデータの種類を生成するかどうか (@p) TT とは異なる (@p)、型推論アルゴリズムでは、この電子メールのデータ型から余分な暗黙的な変換では考慮 (@p) TT に (@p)。  
  
     例:  
  
    ```  
    SELECT * FROM t WHERE Col_Int = Col_Int + @p  
    ```  
  
     この場合、E (@p) は Col_Int +@pおよび TT (@p) は**int**です。**int**に選択されている@p暗黙的な変換が生成されないためです。 その他のデータ型を選択すると、少なくとも 1 つの暗黙的な変換が生成されます。  
  
2.  変換の数が最小となるデータ型が複数ある場合は、優先順位の高いデータ型が使用されます。 次に例を示します。  
  
    ```  
    SELECT * FROM t WHERE Col_Int = Col_smallint + @p  
    ```  
  
     この場合、 **int**と**smallint** 1 つの変換を生成します。 他のすべてのデータ型では、2 つ以上の変換が生成されます。 **Int**よりも優先**smallint**、 **int**はため@pです。 データ型の優先順位の詳細については、次を参照してください。[データ型の優先順位 &#40;です。TRANSACT-SQL と #41 です;](../../t-sql/data-types/data-type-precedence-transact-sql.md)。  
  
     このルールは、ルール 1 に該当するすべてのデータ型と、最高位の優先順位を持つデータ型との間に暗黙的な変換がある場合にのみ適用されます。 暗黙的な変換がない場合、データ型の推論はエラーで失敗します。 たとえば、クエリで`SELECT @p FROM t`、任意のデータの型のためのデータ型の推論は失敗@p同等になります。 たとえばからの暗黙的な変換はありません**int**に**xml**です。  
  
3.  かどうかのような 2 つのデータ型にリンク付けルール 1、たとえば**varchar (8000)**と**varchar (max)**、小さいデータ型 (**varchar (8000)**) を選択します。 同じ原則に適用されます**nvarchar**と**varbinary**データ型。  
  
4.  ルール 1 のために、型推論アルゴリズムでは、特定の変換が他の変換よりも優先されます。 変換の優先順序は、次のとおりです。  
  
    1.  長さの異なる同じ基本データ型間での変換。  
  
    2.  同じデータ型の固定長および可変長のバージョン間の変換 (例: **char**に**varchar**)。  
  
    3.  間の変換**NULL**と**int**です。  
  
    4.  その他の変換。  
  
 たとえば、クエリ`SELECT * FROM t WHERE [Col_varchar(30)] > @p`、 **varchar (8000)**変換 (a) をお勧めするために選択します。 クエリの`SELECT * FROM t WHERE [Col_char(30)] > @p`、 **varchar (8000)**ためと、(b) の型変換が発生するために選択がまだ他の選択肢 (など**(4000)**) 変換の種類 (d) が発生します。  
  
 最後の例として、クエリについて考えてみます`SELECT NULL + @p`、 **int**に選択されている@p型 (c) 変換の結果となるためです。  
  
## <a name="permissions"></a>Permissions  
 実行する権限が必要です、@tsql引数。  
  
## <a name="examples"></a>使用例  
 次の例は、宣言されていない `@id` パラメーターおよび `@name` パラメーターに対して予期されるデータ型などの情報を返します。  
  
```  
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR name = @name'  
  
```  
  
 `@id` パラメーターが `@params` 参照として指定された場合は、`@id` パラメーターは結果セットから省略され、`@name` パラメーターのみが記述されます。  
  
```  
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR NAME = @name',  
@params = N'@id int'  
  
```  
  
## <a name="see-also"></a>参照  
 [sp_describe_first_result_set &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set_for_object &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)  
  
  
