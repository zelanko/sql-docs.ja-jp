---
title: sp_describe_undeclared_parameters (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_undeclared_parameters
- sp_describe_undeclared_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_undeclared_parameters
ms.assetid: 6f016da6-dfee-4228-8b0d-7cd8e7d5a354
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8194c74acb14a78482cc1e1de8fae38682699d3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679639"
---
# <a name="spdescribeundeclaredparameters-transact-sql"></a>sp_describe_undeclared_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  宣言されていないパラメーターに関するメタデータを含む結果セットを返します、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 使用されている各パラメーターの検討、  **\@tsql**バッチで宣言されていないが、  **\@params**します。 これらの各パラメーターに対して 1 行のデータを含む結果セットが返されます。そのパラメーターについて推論される型の情報も含まれます。 空の結果セットを返し、  **\@tsql**入力バッチで宣言されている以外のパラメーターを持たない **\@params**します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql
  
sp_describe_undeclared_parameters   
    [ @tsql = ] 'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' data type ] [, ...n]  
```  
  
## <a name="arguments"></a>引数  
 [  **\@tsql =** ] **'**_TRANSACT-SQL\_バッチ_**'**  
 1 つまたは複数[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。 *Transact SQL_batch*あります**nvarchar (**_n_**)** または**nvarchar (max)** します。  
  
 [  **\@params =** ] **N'**_パラメーター_**'**  
 \@params パラメーターの宣言文字列の提供、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチは、sp_executesql と同様に動作します。 *パラメーター*あります**nvarchar (**_n_**)** または**nvarchar (max)** します。  
  
 1 つの文字列に埋め込まれたすべてのパラメーターの定義を含む*Transact SQL_batch*します。 この文字列は Unicode 定数または Unicode 変数にする必要があります。 各パラメーター定義は、パラメーター名とデータ型で構成されます。 n は、追加のパラメーター定義を示すプレースホルダーです。 TRANSACT-SQL ステートメントまたはステートメント内のバッチが、パラメーターが含まれない場合\@params は必要ありません。 このパラメーターの既定値は NULL です。  
  
 データ型  
 パラメーターのデータ型です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **sp_describe_undeclared_parameters**返しますが常に成功した場合に 0 の状態を返します。 プロシージャは、エラーをスローします。 プロシージャが RPC として呼び出された場合は、戻り値の状態は sys.dm_exec_describe_first_result_set の error_type 列」の説明に従って、エラーの種類によって設定されます。 プロシージャが呼び出された場合[!INCLUDE[tsql](../../includes/tsql-md.md)]、戻り値は、エラーの場合であっても、0 では常にします。  
  
## <a name="result-sets"></a>結果セット  
 **sp_describe_undeclared_parameters**次の結果セットを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int NOT NULL**|結果セット内のパラメーターの位置を示す序数を格納します。 最初のパラメーターの位置は 1 で指定されます。|  
|**name**|**sysname は NOT NULL**|パラメーターの名前を格納します。|  
|**suggested_system_type_id**|**int NOT NULL**|含まれています、 **system_type_id** sys.types で指定されたパラメーターのデータ型。<br /><br /> CLR の型の場合でも、 **system_type_name**列は NULL を返して、この列は値 240 を返します。|  
|**suggested_system_type_name**|**nvarchar (256) NULL**|データ型の名前を格納します。 パラメーターのデータ型に指定されている引数 (長さ、有効桁数、小数点以下桁数など) を含みます。 データ型がユーザー定義の別名型の場合は、基になるシステム型がここで指定されます。 CLR ユーザー定義データ型である場合は、この列で NULL が返されます。 パラメーターの型を推論できない場合は、NULL が返されます。|  
|**suggested_max_length**|**smallint NOT NULL**|Sys.columns を参照してください。 **max_length**列の説明。|  
|**suggested_precision**|**tinyint NOT NULL**|Sys.columns を参照してください。 有効桁数の列の説明。|  
|**suggested_scale**|**tinyint NOT NULL**|Sys.columns を参照してください。 スケールの列の説明。|  
|**suggested_user_type_id**|**int NULL**|CLR 型と別名型の場合、sys.types で指定された列のデータ型の user_type_id を格納します。 それ以外の場合は NULL です。|  
|**suggested_user_type_database**|**sysname NULL**|CLR 型と別名型の場合、その型が定義されたデータベースの名前を格納します。 それ以外の場合は NULL です。|  
|**suggested_user_type_schema**|**sysname NULL**|CLR 型と別名型の場合、その型が定義されたスキーマの名前を格納します。 それ以外の場合は NULL です。|  
|**suggested_user_type_name**|**sysname NULL**|CLR 型と別名型の場合、その型の名前を格納します。 それ以外の場合は NULL です。|  
|**suggested_assembly_qualified_type_name**|**nvarchar (4000) NULL**|CLR 型には、アセンブリと型を定義するクラスの名前を返します。 それ以外の場合は NULL です。|  
|**suggested_xml_collection_id**|**int NULL**|Sys.columns で指定されたパラメーターのデータ型の xml_collection_id を格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_xml_collection_database**|**sysname NULL**|この型に関連付けられている XML スキーマ コレクションが定義されているデータベースを格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_xml_collection_schema**|**sysname NULL**|この型に関連付けられている XML スキーマ コレクションが定義されているスキーマを格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_xml_collection_name**|**sysname NULL**|この型に関連付けられている XML スキーマ コレクションの名前を格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**suggested_is_xml_document**|**bit NOT NULL**|返される型が XML とその型の XML ドキュメントのことが保証されている場合は、1 を返します。 それ以外の場合 0 を返します。|  
|**suggested_is_case_sensitive**|**bit NOT NULL**|列がない場合に大文字の文字列型で、0 の場合は、1 を返します。|  
|**suggested_is_fixed_length_clr_type**|**bit NOT NULL**|この列が固定長の CLR 型の場合は 1、それ以外の場合は 0 を返します。|  
|**suggested_is_input**|**bit NOT NULL**|パラメーターが、代入の左辺以外の場所で使用される場合は 1 を返します。 それ以外の場合 0 を返します。|  
|**suggested_is_output**|**bit NOT NULL**|パラメーターが代入の左辺で使用される場合、またはストアド プロシージャの出力パラメーターに渡される場合は 1 を返します。 それ以外の場合 0 を返します。|  
|**formal_parameter_name**|**sysname NULL**|パラメーターがストアド プロシージャまたはユーザー定義関数の引数の場合は、対応する仮パラメーターの名前を返します。 それ以外の場合、NULL を返します。|  
|**suggested_tds_type_id**|**int NOT NULL**|内部使用です。|  
|**suggested_tds_length**|**int NOT NULL**|内部使用です。|  
  
## <a name="remarks"></a>コメント  
 **sp_describe_undeclared_parameters**返しますが常にステータス 0 を返します。  
  
 最も一般的な使用方法は、パラメーターを含み、それらのパラメーターを任意の方法で処理する必要がある [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがアプリケーションで指定される場合です。 例は、ユーザー インターフェイス (ODBCTest または RowsetViewer) など、ユーザーが ODBC パラメーターの構文を使用してクエリを提供します。 このような場合、アプリケーションは動的にパラメーターの数を検出し、それぞれのパラメーターに対してユーザーに入力を求める必要があります。  
  
 別の例として、ユーザー入力なしで、アプリケーションがパラメーターをループして、そのデータを他の場所 (テーブルなど) から取得する必要がある場合が挙げられます。 この場合は、アプリケーションはすべてのパラメーター情報を一度に渡す必要はありません。 代わりに、アプリケーションはプロバイダーからすべてのパラメーター情報を取得し、データ自体はテーブルから取得することができます。 使用してコード**sp_describe_undeclared_parameters**はより汎用的可能性が低い場合は、データ構造の変更が後で変更が必要です。  
  
 **sp_describe_undeclared_parameters**場合は、次のいずれかでエラーが返されます。  
  
-   場合、入力\@tsql が有効ではありません[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 有効性は、解析および分析によって決まりますが、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 クエリの最適化中または実行中に、バッチによるエラーは、決定する際に考慮されないかどうか、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチが有効です。  
  
-   場合\@1 回以上のパラメーターを宣言する文字列が含まれている場合、またはパラメーターが NULL でないと、パラメーターの宣言の構文が有効な文字列でない文字列が含まれています。  
  
-   場合、入力[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチで宣言されているパラメーターに同じ名前のローカル変数を宣言します\@params します。  
  
- ステートメントは、一時テーブルを参照している場合。
  
 場合\@tsql がで宣言されている以外のパラメーターを持たない\@params、プロシージャは、空の結果セットを返します。  
  
## <a name="parameter-selection-algorithm"></a>パラメーター選択アルゴリズム  
 宣言されていないパラメーターを持つクエリの場合、宣言されていないパラメーターのデータ型の推論は 3 つの手順で実行されます。  
  
 **手順 1**  
  
 宣言されていないパラメーターを持つクエリのデータ型の推論の最初の手順は、宣言されていないパラメーターに依存しないデータ型を持つすべてのサブ式のデータ型を見つけることです。 型は次の式に対して特定できます。  
  
-   列、定数、変数、および宣言されたパラメーター。  
  
-   ユーザー定義関数 (UDF) の呼び出しの結果。  
  
-   すべての入力について、宣言されていないパラメーターに依存しないデータ型を持つ式。  
  
 たとえば、クエリ`SELECT dbo.tbl(@p1) + c1 FROM t1 WHERE c2 = @p2 + 2`します。 式 dbo.tbl (\@p1) + c1 と c2 があるデータ型、および式\@p1 と\@p2 + 2 はありません。  
  
 この手順の実行後、UDF の呼び出し以外の任意の式に、データ型のない 2 つの引数が含まれている場合、型推論はエラーで失敗します。 たとえば、次のすべての式ではエラーが発生します。  
  
```sql
SELECT * FROM t1 WHERE @p1 = @p2  
SELECT * FROM t1 WHERE c1 = @p1 + @p2  
SELECT * FROM t1 WHERE @p1 = SUBSTRING(@p2, 2, 3)  
```  
  
 次の例ではエラーは発生しません。  
  
```sql
SELECT * FROM t1 WHERE @p1 = dbo.tbl(c1, @p2, @p3)  
```
  
 **手順 2**  
  
 指定された宣言されていないパラメーター \@p、型推論アルゴリズムは、最も内側の式 E を検索します (\@p) を格納している\@p は、次のいずれか。  
  
-   比較演算子または代入演算子の引数。  
  
-   ユーザー定義関数 (テーブル値 UDF を含む)、プロシージャ、またはメソッドの引数。  
  
-   引数を**値**の句、**挿入**ステートメント。  
  
-   引数を**キャスト**または**変換**します。  
  
 型推論アルゴリズムは検索対象のデータ型 TT (\@p) e (\@p)。 前の例の場合、対象のデータ型は以下のとおりです。  
  
-   比較または代入の反対側のデータ型。  
  
-   この引数が渡されるパラメーターの宣言されたデータ型。  
  
-   この値が挿入される列のデータ型。  
  
-   このステートメントがキャストまたは変換するデータ型。  
  
 たとえば、クエリ`SELECT * FROM t WHERE @p1 = dbo.tbl(@p2 + c1)`します。 E し (\@p1) = \@p1、E (\@p2) = \@p2 + c1、TT (\@p1) TT dbo.tbl の宣言された戻り値のデータ型は、(\@p2) は dbo.tbl の宣言されたパラメーター データ型です。  
  
 場合\@p が、手順 2. の冒頭で紹介した、型推論アルゴリズムを決定する任意の式に含まれていないその E (\@p) を含む最大のスカラー式は、 \@p、および、型推論アルゴリズムはありません計算対象のデータ型 TT (\@p) e (\@p)。 たとえば、次のクエリが SELECT `@p + 2` 、E (\@p) = \@p + 2、TT はありません (\@p)。  
  
 **手順 3**  
  
 E ようになりました (\@p) と TT (\@p) は、型推論アルゴリズムは推測のデータ型を識別、 \@p で、次の 2 つの方法のいずれか。  
  
-   単純な推論  
  
     場合 E (\@p) = \@p、TT (\@p) 場合に、存在する、つまり\@p が直接、式の 1 つの引数は、手順 2. の冒頭に記載されている、型推論アルゴリズムのデータ型を推測\@を TT (p\@p)。 以下に例を示します。  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p1 AND @p2 = dbo.tbl(@p3)  
    ```  
  
     データ型\@p1、 \@p2、および\@p3 は c1、dbo.tbl の戻り値のデータ型のデータ型になるし、それぞれ dbo.tbl のパラメーター データ型します。  
  
     特殊なケースとして場合\@p は、引数、 \<、>、 \<=、または > = 演算子、単純な推論のルールは適用されません。 型推論アルゴリズムは、次のセクションで説明する一般的な推論のルールを使用します。 たとえば、c1 がデータ型 char(30) の列である場合に、以下の 2 つのクエリについて考えてみます。  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p  
    SELECT * FROM t WHERE c1 > @p  
    ```  
  
     最初のケースで、型推論アルゴリズムは**char (30)** のデータ型として\@このトピックの「ルールに従って p。 2 番目のケースで、型推論アルゴリズムは**varchar (8000)** 次のセクションで、一般的な推論規則に従ってします。  
  
-   一般的な推論  
  
     単純な推論が適用されない場合、次のデータ型は宣言されていないパラメーターと見なされます。  
  
    -   整数データ型 (**ビット**、 **tinyint**、 **smallint**、 **int**、 **bigint**)  
  
    -   Money データ型 (**smallmoney**、 **money**)  
  
    -   浮動小数点データ型 (**float**、**実際**)  
  
    -   **numeric (38, 19)** -その他の numeric または decimal データ型は考慮されません。  
  
    -   **varchar (8000)**、 **varchar (max)**、 **nvarchar (4000)**、および**nvarchar (max)** - その他の文字列データ型 (など**テキスト**、 **char (8000)**、 **nvarchar (30)** など) とは見なされません。  
  
    -   **varbinary (8000)** と**varbinary (max)** -その他のバイナリ データ型は考慮されません (など**イメージ**、 **binary(8000)**、 **varbinary(30)** など。)。  
  
    -   **日付**、 **time (7)**、 **smalldatetime**、 **datetime**、 **datetime2 (7)**、 **datetimeoffset (7)** - その他の日付し、時刻のなどの種類、 **time(4)** とは見なされません。  
  
    -   **sql_variant**  
  
    -   **xml**  
  
    -   CLR システム定義型 (**hierarchyid**、 **geometry**、 **geography**)  
  
    -   CLR ユーザー定義型  
  
### <a name="selection-criteria"></a>選択基準  
 候補のデータ型のうち、クエリを無効にするデータ型は拒否されます。 候補の残りのデータ型から、型推論アルゴリズムが次のルールに従って 1 つを選択します。  
  
1.  E の暗黙的な変換の最小数を生成するデータ型 (\@p) を選択します。 特定のデータ型が E のデータ型を生成するかどうか (\@p) TT とは異なる (\@p) を型推論アルゴリズムは E のデータ型から余分な暗黙的な変換にこれと見なします (\@p) に TT (\@p)。  
  
     以下に例を示します。  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_Int + @p  
    ```  
  
     この場合、E (\@p) は Col_Int + \@p、TT (\@p) は**int**します。**int**選択\@p ため、暗黙的な変換は生成されません。 その他のデータ型を選択すると、少なくとも 1 つの暗黙的な変換が生成されます。  
  
2.  変換の数が最小となるデータ型が複数ある場合は、優先順位の高いデータ型が使用されます。 次に例を示します。  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_smallint + @p  
    ```  
  
     この場合、 **int**と**smallint** 1 つの変換を生成します。 他のすべてのデータ型では、2 つ以上の変換が生成されます。 **Int**よりも優先**smallint**、 **int**使用\@p。 データ型の優先順位の詳細については、次を参照してください。[データ型の優先順位&#40;TRANSACT-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)します。  
  
     このルールは、ルール 1 に該当するすべてのデータ型と、最高位の優先順位を持つデータ型との間に暗黙的な変換がある場合にのみ適用されます。 暗黙的な変換がない場合、データ型の推論はエラーで失敗します。 たとえば、クエリで`SELECT @p FROM t`、任意のデータの型のためのデータ型の推論は失敗\@p は同等になります。 たとえばからの暗黙的変換がない**int**に**xml**します。  
  
3.  かどうかのような 2 つのデータ型にリンク付けルール 1、たとえば**varchar (8000)** と**varchar (max)**、小さい方のデータ型 (**varchar (8000)**) が選択されます。 同じ原則に適用されます**nvarchar**と**varbinary**データ型。  
  
4.  ルール 1 のために、型推論アルゴリズムでは、特定の変換が他の変換よりも優先されます。 変換の優先順序は、次のとおりです。  
  
    1.  長さの異なる同じ基本データ型間での変換。  
  
    2.  同じデータ型の固定長および可変長のバージョン間の変換 (例: **char**に**varchar**)。  
  
    3.  間の変換**NULL**と**int**します。  
  
    4.  その他の変換。  
  
 たとえば、クエリ`SELECT * FROM t WHERE [Col_varchar(30)] > @p`、 **varchar (8000)** 変換 (a) が最適なために選択します。 クエリの`SELECT * FROM t WHERE [Col_char(30)] > @p`、 **varchar (8000)** 、(b) の型変換が発生するため、まだ選択別の選択肢 (など**varchar(4000)**) 変換の種類 (d) になります。  
  
 最後の例として、クエリを指定`SELECT NULL + @p`、 **int**選択\@p (c) の型変換の結果となるためです。  
  
## <a name="permissions"></a>アクセス許可  
 実行する権限が必要です、 \@tsql 引数。  
  
## <a name="examples"></a>使用例  
 次の例は、宣言されていない `@id` パラメーターおよび `@name` パラメーターに対して予期されるデータ型などの情報を返します。  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR name = @name'  
  
```  
  
 `@id` パラメーターが `@params` 参照として指定された場合は、`@id` パラメーターは結果セットから省略され、`@name` パラメーターのみが記述されます。  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR NAME = @name',  
@params = N'@id int'  
  
```  
  
## <a name="see-also"></a>参照  
 [sp_describe_first_result_set &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)
