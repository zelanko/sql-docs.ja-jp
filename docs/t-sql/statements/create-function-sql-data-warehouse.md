---
title: "CREATE FUNCTION (SQL データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8cad1b2c-5ea0-4001-9060-2f6832ccd057
caps.latest.revision: 14
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 55f1b7e612a1c7d120e06078b0fdba45d6409d36
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-function-sql-data-warehouse"></a>関数 (SQL データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] でユーザー定義関数を作成します。 ユーザー定義関数は、[!INCLUDE[tsql](../../includes/tsql-md.md)]ルーチン パラメーターを受け取るが、複雑な計算などの操作を実行し、値として、そのアクションの結果を返します。 戻り値は、スカラー (単一) 値である必要があります。 このステートメントを使用して、次の方法で使用できる再利用可能なルーチンを作成します。  
  
-   SELECT などの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内で使用する  
  
-   関数を呼び出すアプリケーション内で使用する  
  
-   別のユーザー定義関数の定義内で使用する  
  
-   列の CHECK 制約を定義する  
  
-   ストアド プロシージャを置換する  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
--Transact-SQL Scalar Function Syntax  
CREATE FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]  
  
<function_option>::=   
{  
    [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
}  
  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 ユーザー定義関数が属するスキーマの名前を指定します。  
  
 *function_name*  
 ユーザー定義関数の名前です。 関数名では、識別子の規則に従う必要があり、およびそのスキーマ、データベース内で一意である必要があります。  
  
> [!NOTE]  
>  パラメーターを指定しない場合でも、関数名の後にはかっこが必要です。  
  
 @*parameter_name*  
 ユーザー定義関数内のパラメーターです。 1 つ以上のパラメーターを宣言できます。  
  
 1 つの関数では、最高 2,100 個のパラメーターを使用できます。 宜言した各パラメーターの値は、関数の実行時に、ユーザーが指定する必要があります (そのパラメーターの既定値が定義されていない場合)。  
  
 最初の文字をアット マーク (@) にしてパラメーター名を指定します。 パラメーター名は識別子のルールに従っている必要があります。 パラメーターは関数に対してローカルです。同じパラメーター名を他の関数で使用できます。 パラメーターは定数の代わりとしてのみ使用できます。パラメーターは、テーブル名、列名、またはその他のデータベース オブジェクト名の代わりに使用することはできません。  
  
> [!NOTE]  
>  ストアド プロシージャまたはユーザー定義関数でパラメーターを渡すとき、あるいはバッチ ステートメントで変数を宣言して設定するときには、ANSI_WARNINGS が無視されます。 たとえば、として変数が定義されている**char (3)**とし、次の 3 つの文字を超える値に設定、データは切り捨てに定義されているサイズと、INSERT または UPDATE ステートメントは成功します。  
  
 *parameter_data_type*  
 パラメーターのデータ型です。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数でサポートされるすべてのスカラー データ型[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]は許可されています。 タイムスタンプ (rowversion) データ型はサポートされていません。  
  
 [=*既定*]  
 パラメーターの既定値です。 場合、*既定*値は、そのパラメーターの値を指定せず、関数を実行することができます。  
  
 関数のパラメーターに既定値がある場合に、既定値を取得する目的でその関数を呼び出すときは、DEFAULT キーワードを指定する必要があります。 この動作は、ストアド プロシージャで既定値を持つパラメーターを使用する場合とは異なります。ストアド プロシージャの場合は、パラメーターを省略すると既定値が暗黙的に使用されます。  
  
 *return_data_type*  
 スカラー ユーザー定義関数の戻り値です。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数でサポートされるすべてのスカラー データ型[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]は許可されています。 タイムスタンプ (rowversion) データ型はサポートされていません。 カーソルとテーブルのスカラー型を指定することはできません。  
  
 *function_body*  
 一連の[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  Function_body は SELECT ステートメントを含めることはできませんし、データベースのデータを参照することはできません。  Function_body には、テーブルまたはビューを参照できません。 関数の本体では、その他の決定的な関数を呼び出すことができますが、非決定的関数を呼び出すことはできません。 
  
 スカラー関数は、 *function_body*一連の[!INCLUDE[tsql](../../includes/tsql-md.md)]スカラー値にまとめて評価されるステートメントです。  
  
 *scalar_expression*  
 スカラー関数が返すスカラー値を指定します。  
  
 **\<function_option >:: =** 
  
 関数が、次のオプションの 1 つ以上を持つことを指定します。  
  
 SCHEMABINDING  
 参照するデータベース オブジェクトに対して、その関数がバインドされるように指定します。 SCHEMABINDING を指定した場合、ベース オブジェクトに対して関数定義に影響を与えるような変更は行えません。 まず関数定義を変更または削除して、変更するオブジェクトとの依存関係を解消する必要があります。  
  
 関数からその参照先のオブジェクトへのバインドは、次のいずれかの操作が行われた場合にのみ削除されます。  
  
-   関数を削除した場合。  
  
-   関数を、SCHEMABINDING オプションを指定せずに ALTER ステートメントを使用して変更した場合。  
  
 関数をスキーマにバインドできるのは、次の条件が満たされている場合に限られます。  
  
-   関数によって参照されているすべてのユーザー定義関数もスキーマにバインドします。  
  
-   関数は、およびその他のユーザー定義関数の関数が参照は、1 つまたは 2 部構成の名前を使用して参照されます。  
  
-   のみの組み込み関数と同じデータベース内には、その他の Udf は、ユーザー定義関数の本体で参照できます。  
  
-   CREATE FUNCTION ステートメントを実行したユーザーが、その関数が参照するデータベース オブジェクトに対する REFERENCES 権限を持っている。  
  
 SCHEMABINDING を使用して変更を削除するには  
  
 NULL 入力時に NULL を返します |**NULL 入力時に呼び出されます**  
 指定します、 **OnNULLCall**スカラー値関数の属性です。 指定しない場合は、既定で CALLED ON NULL INPUT が暗黙的に使用されます。 つまり、NULL が引数として渡された場合でも、関数本体が実行されます。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ユーザー定義関数の作成時に SCHEMABINDING 句を使用しないと、基になるオブジェクトに加えられた変更が関数の定義に影響して、関数が呼び出されたときに予期しない結果が生じる可能性があります。 基になるオブジェクトに対する変更によって関数が古くならないように、次のいずれかの操作を行うことをお勧めします。  
  
-   関数を作成するときに WITH SCHEMABINDING 句を指定します。 これにより、関数定義で参照されているオブジェクトは、一緒に関数も変更しない限り変更できなくなります。  
  
## <a name="interoperability"></a>相互運用性  
 関数で有効なステートメントは以下のとおりです。  
  
-   代入ステートメント。  
  
-   TRY...CATCH ステートメント以外の流れ制御ステートメント。  
  
-   ローカル データ変数を定義するステートメントを宣言します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 ユーザー定義関数は、データベースの状態を変更するアクションの実行に使用することはできません。  
  
 ユーザー定義関数は入れ子にすることができます。つまり、1 つのユーザー定義関数で、別のユーザー定義関数を呼び出すことができます。 呼び出された関数が実行を開始すると入れ子レベルが 1 つ上がり、呼び出された関数が実行を終了するとレベルが 1 つ下がります。 ユーザー定義関数は、32 レベルまで入れ子にすることができます。 入れ子レベルが最大値を超えると、関数チェーン全体の呼び出しが失敗します。   
  
## <a name="metadata"></a>メタデータ  
 このセクションでは、ユーザー定義関数に関するメタデータを返すに使用できるシステム カタログ ビューを一覧表示します。  
  
 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) : の定義を表示[!INCLUDE[tsql](../../includes/tsql-md.md)]ユーザー定義関数です。 例:  
  
```  
SELECT definition, type   
FROM sys.sql_modules AS m  
JOIN sys.objects AS o   
    ON m.object_id = o.object_id   
    AND type = ('FN');  
GO  
  
```  
  
 [sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) : ユーザー定義関数で定義されているパラメーターに関する情報が表示されます。  
  
 [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) : 関数が参照する基になるオブジェクトが表示されます。  
  
## <a name="permissions"></a>Permissions  
 データベースの CREATE FUNCTION 権限と、関数を作成するスキーマの ALTER 権限が必要です。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-a-scalar-valued-user-defined-function-to-change-a-data-type"></a>A. ユーザー定義のスカラー値関数を使用して、データ型を変更するには  
 この単純な関数には、 **int**データ型として、入力を返す、 **decimal(10,2)**出力としてのデータ型。  
  
```  
CREATE FUNCTION dbo.ConvertInput (@MyValueIn int)  
RETURNS decimal(10,2)  
AS  
BEGIN  
    DECLARE @MyValueOut int;  
    SET @MyValueOut= CAST( @MyValueIn AS decimal(10,2));  
    RETURN(@MyValueOut);  
END;  
GO  
  
SELECT dbo.ConvertInput(15) AS 'ConvertedValue';  
```  
  
## <a name="see-also"></a>参照  
 [ALTER FUNCTION (SQL Server PDW)](http://msdn.microsoft.com/en-us/25ff3798-eb54-4516-9973-d8f707a13f6c)   
 [関数 (SQL Server PDW) を削除します](http://msdn.microsoft.com/en-us/1792a90d-0d06-4852-9dec-6de1b9cd229e)  
  
  



