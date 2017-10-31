---
title: "次に (TRANSACT-SQL) の値 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEXT_VALUE_TSQL
- NEXT
- NEXT VALUE
- NEXT VALUE FOR
- NEXT_TSQL
- NEXT_VALUE_FOR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEXT VALUE FOR function
- sequence number object, NEXT VALUE FOR function
ms.assetid: 92632ed5-9f32-48eb-be28-a5e477ef9076
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aab8020fa04b978d7ec1b657fe0a1084123dfb48
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="next-value-for-transact-sql"></a>NEXT VALUE FOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  指定したシーケンス オブジェクトからシーケンス番号を生成します。  
  
 両方の作成とシーケンスの使用の詳細については、次を参照してください。[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)です。 使用して[sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)を生成するシーケンス番号の範囲を予約します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
NEXT VALUE FOR [ database_name . ] [ schema_name . ]  sequence_name  
   [ OVER (<over_order_by_clause>) ]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 シーケンス オブジェクトを含むデータベースの名前を指定します。  
  
 *schema_name*  
 シーケンス オブジェクトを含むスキーマの名前を指定します。  
  
 *sequence_name*  
 番号を生成するシーケンス オブジェクトの名前を指定します。  
  
 *over_order_by_clause*  
 シーケンス値がパーティション内の行に割り当てられる順序を決定します。 詳細については、次を参照してください。 [OVER 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>戻り値の型  
 シーケンスの型を使用して数値を返します。  
  
## <a name="remarks"></a>解説  
 **NEXT VALUE FOR**関数は、ストアド プロシージャやトリガーで使用できます。  
  
 ときに、 **NEXT VALUE FOR**同じシーケンス オブジェクトが複数回使用されている場合、または、値を提供するステートメントとの両方で既定の制約で同じシーケンス オブジェクトを使用する場合に、クエリや既定の制約で使用される関数実行中に、同じ値が返されます、結果セット内の行で同じシーケンスを参照するすべての列。  
  
 **NEXT VALUE FOR**関数は、非決定的であり、生成されるシーケンス値の数が適切に定義されたコンテキストでのみ使用します。 特定のステートメントにおいて、参照されている各シーケンス オブジェクトに使用される値の数の定義を以下に示します。  
  
-   **選択**-参照されているシーケンス オブジェクトごとに、新しい値が 1 回生成、ステートメントの結果内の行ごとです。  
  
-   **挿入**しています. **値**-参照されているシーケンス オブジェクトごとに、新しい値が 1 回生成、ステートメントで挿入された行はごとです。  
  
-   **更新**-、参照されているシーケンス オブジェクトごとに新しい値は、ステートメントによって更新された行ごとに生成します。  
  
-   手続き型ステートメント (など**DECLARE**、**設定**など) のステートメントごとに、参照されているシーケンス オブジェクトごとに新しい値を生成します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 **NEXT VALUE FOR**関数は、次の状況では使用できません。  
  
-   データベースが読み取り専用モードの場合。  
  
-   テーブル値関数の引数として使用する場合。  
  
-   集計関数の引数として使用する場合。  
  
-   共通テーブル式および派生テーブルを含むサブクエリ内で使用する場合。  
  
-   ビュー、ユーザー定義関数、または計算列内で使用する場合。  
  
-   使用するステートメントで、 **DISTINCT**、**共用体**、 **UNION ALL**、 **EXCEPT**または**INTERSECT**演算子。  
  
-   使用するステートメントで、 **ORDER BY**句しない限り、 **NEXT VALUE FOR**しています. **経由で**(**ORDER BY** ...) を使用します。  
  
-   次の句で:**フェッチ**、**経由で**、**出力**、 **ON**、 **PIVOT**、 **UNPIVOT**、 **GROUP BY**、 **HAVING**、**コンピューティング**、 **COMPUTE BY**、または**FOR XML**.  
  
-   使用して条件式で**ケース**、**選択**、 **COALESCE**、 **IIF**、 **ISNULL**、または**NULLIF**です。  
  
-   **値**ではない句の一部、**挿入**ステートメントです。  
  
-   CHECK 制約の定義で使用する場合。  
  
-   ルールまたは既存のオブジェクトの定義で使用する場合  (既定の制約では使用できます)。  
  
-   既定では、ユーザー定義テーブル型で使用します。  
  
-   ステートメントを使用して、**上部**、**オフセット**、または、 **ROWCOUNT**オプションを設定します。  
  
-   **場所**ステートメントの句。  
  
-   **マージ**ステートメントです。 (する場合を除く、 **NEXT VALUE FOR**関数はターゲット テーブルの既定の制約で使用され、既定値で使用、**作成**のステートメント、**マージ**ステートメントです)。  
  
## <a name="using-a-sequence-object-in-a-default-constraint"></a>既定の制約でのシーケンス オブジェクトの使用  
 使用する場合、 **NEXT VALUE FOR**関数既定の制約では、次の規則が適用されます。  
  
-   複数のテーブル内の既定の制約から 1 つのシーケンス オブジェクトを参照できます。  
  
-   テーブルとシーケンス オブジェクトは同じデータベースに置く必要があります。  
  
-   既定の制約を追加するユーザーには、シーケンス オブジェクトに対する REFERENCES 権限が必要です。  
  
-   既定の制約を削除する前に、既定の制約から参照されているシーケンス オブジェクトを削除できません。  
  
-   複数の既定の制約で同じシーケンス オブジェクトを使用する場合、または値を提供するステートメントと実行中の既定の制約の両方で同じシーケンス オブジェクトを使用する場合、行内のすべての列に対して同じシーケンス番号が返されます。  
  
-   参照、 **NEXT VALUE FOR**既定の制約で関数を指定できません、**経由で**句。  
  
-   既定の制約で参照されているシーケンス オブジェクトは変更できます。  
  
-   場合、`INSERT … SELECT`または`INSERT … EXEC`ステートメントを使用してクエリから挿入されるデータの取得、 **ORDER BY**句、によって返される値、 **NEXT VALUE FOR**関数指定された順序で生成された、 **ORDER BY**句。  
  
## <a name="using-a-sequence-object-with-an-over-order-by-clause"></a>OVER ORDER BY 句でのシーケンス オブジェクトの使用  
 **NEXT VALUE FOR**関数では、適用することにより並べ替えられたシーケンス値の生成、**経由で**句を**NEXT VALUE FOR**呼び出します。 使用して、**経由で**句が保証の順序で返される値が生成される、**経由で**句の**順序 B**Y のサブ句。 次の追加の規則の適用を使用する場合、 **NEXT VALUE FOR**で機能、**経由で**句。  
  
-   複数回呼び出す、 **NEXT VALUE FOR**関数の 1 つのステートメントで同じシーケンス ジェネレーター必要がありますすべてを使用して、同じの**経由で**句の定義。  
  
-   複数回呼び出す、 **NEXT VALUE FOR**関数の 1 つのステートメントで異なるシーケンス ジェネレーターの参照を持つことができるさまざまな**経由で**句の定義。  
  
-   **経由で**句に適用される、 **NEXT VALUE FOR**関数がサポートされていません、 **PARTITION BY**サブ句。  
  
-   すべての呼び出しの場合、 **NEXT VALUE FOR**で機能、**選択**ステートメントを指定します、**経由で**句、 **ORDER BY**句で使用します。**選択**ステートメントです。  
  
-   **経由で**で使用できる句は、 **NEXT VALUE FOR**関数で使用する場合、**選択**ステートメントまたは`INSERT … SELECT …`ステートメントです。 使用、**経由で**句、 **NEXT VALUE FOR**で関数が許可されません**更新**または**マージ**ステートメントです。  
  
-   別のプロセスが同時にシーケンス オブジェクトにアクセスしている場合は、非連続的な番号が返される可能性があります。  
  
## <a name="metadata"></a>メタデータ  
 シーケンスについては、クエリ、 [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)カタログ ビューです。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**更新**シーケンス オブジェクトまたはシーケンスのスキーマに対する権限。 権限を付与する例については、後の例 F を参照してください。  
  
### <a name="ownership-chaining"></a>所有権の継承  
 シーケンス オブジェクトでは、組み合わせ所有権をサポートしています。 シーケンス オブジェクトの所有者が、(既定の制約としてシーケンス オブジェクトを所有する) 呼び出し元のストアド プロシージャ、トリガー、またはテーブルと同じ場合、シーケンス オブジェクトに対する権限チェックは必要ありません。 シーケンス オブジェクトの所有者が、呼び出し元のストアド プロシージャ、トリガー、またはテーブルと異なる場合、シーケンス オブジェクトに対する権限チェックが必要です。  
  
 ときに、 **NEXT VALUE FOR**関数がテーブル内の既定値として使用される、ユーザーには、両方が必要とする**挿入**、テーブルに対する権限と**更新**シーケンス オブジェクトに対するアクセス許可、既定値を使用してデータを挿入します。  
  
-   既定の制約の所有者がシーケンス オブジェクトと同じ場合、既定の制約を呼び出す際に、シーケンス オブジェクトに対する権限は必要ありません。  
  
-   既定の制約の所有者がシーケンス オブジェクトと異なる場合、既定の制約を使用してシーケンス オブジェクトを呼び出す際にも、シーケンス オブジェクトに対する権限が必要です。  
  
### <a name="audit"></a>監査  
 監査する、 **NEXT VALUE FOR**関数を SCHEMA_OBJECT_ACCESS_GROUP を監視します。  
  
## <a name="examples"></a>使用例  
 両方のシーケンスを作成および使用の例については、 **NEXT VALUE FOR**を参照してください、シーケンス番号を生成する関数[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)です。  
  
 次の例は、という名前のシーケンスを使用して`CountBy1`という名前のスキーマで`Test`です。 作成する次のステートメントを実行して、`Test.CountBy1`シーケンス。 例 C および E を使用して、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース、ため、`CountBy1`シーケンスはそのデータベースに作成します。  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Test;  
GO  
  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="a-using-a-sequence-in-a-select-statement"></a>A. SELECT ステートメントでシーケンスを使用する  
 次の例では、使用されるたびに 1 つずつ増加する `CountBy1` という名前のシーケンスを作成します。  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1 AS FirstUse;  
SELECT NEXT VALUE FOR Test.CountBy1 AS SecondUse;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FirstUse  
1  
  
SecondUse  
2
```  
  
### <a name="b-setting-a-variable-to-the-next-sequence-value"></a>B. 変数に次のシーケンス値を設定する  
 次の例では、変数にシーケンス番号の次の値を設定する 3 つの方法を示します。  
  
```  
DECLARE @myvar1 bigint = NEXT VALUE FOR Test.CountBy1  
DECLARE @myvar2 bigint ;  
DECLARE @myvar3 bigint ;  
SET @myvar2 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar3 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar1 AS myvar1, @myvar2 AS myvar2, @myvar3 AS myvar3 ;  
GO  
```  
  
### <a name="c-using-a-sequence-with-a-ranking-window-function"></a>C. 順位付け関数と共にシーケンスを使用する  
  
```  
USE AdventureWorks2012 ;  
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 OVER (ORDER BY LastName) AS ListNumber,  
    FirstName, LastName  
FROM Person.Contact ;  
GO  
```  
  
### <a name="d-using-the-next-value-for-function-in-the-definition-of-a-default-constraint"></a>D. 既定の制約の定義で NEXT VALUE FOR 関数を使用する  
 使用して、 **NEXT VALUE FOR**既定の制約の定義の関数はサポートされています。 使用する例については**NEXT VALUE FOR**で、 **CREATE TABLE**ステートメントでは、例 C を参照してください[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)です。 次の例では、`ALTER TABLE` を使用して、シーケンスを既定値として現在のテーブルに追加します。  
  
```  
CREATE TABLE Test.MyTable  
(  
    IDColumn nvarchar(25) PRIMARY KEY,  
    name varchar(25) NOT NULL  
) ;  
GO  
  
CREATE SEQUENCE Test.CounterSeq  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
ALTER TABLE Test.MyTable  
    ADD   
        DEFAULT N'AdvWorks_' +   
        CAST(NEXT VALUE FOR Test.CounterSeq AS NVARCHAR(20))   
        FOR IDColumn;  
GO  
  
INSERT Test.MyTable (name)  
VALUES ('Larry') ;  
GO  
  
SELECT * FROM Test.MyTable;  
GO  
```  
  
### <a name="e-using-the-next-value-for-function-in-an-insert-statement"></a>E. INSERT ステートメントで NEXT VALUE FOR 関数を使用する  
 次の例では、`TestTable` という名前のテーブルを作成した後、`NEXT VALUE FOR` 関数を使用して、行を挿入します。  
  
```  
CREATE TABLE Test.TestTable  
     (CounterColumn int PRIMARY KEY,  
    Name nvarchar(25) NOT NULL) ;   
GO  
  
INSERT Test.TestTable (CounterColumn,Name)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Syed') ;  
GO  
  
SELECT * FROM Test.TestTable;   
GO  
  
```  
  
### <a name="e-using-the-next-value-for-function-with-select--into"></a>E. NEXT VALUE FOR 関数を使用して、SELECT としています. INTO  
 次の例では、`SELECT … INTO`という名前のテーブルを作成するステートメント`Production.NewLocation`を使用して、`NEXT VALUE FOR`各行に番号関数。  
  
```  
USE AdventureWorks2012 ;   
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 AS LocNumber, Name   
    INTO Production.NewLocation  
    FROM Production.Location ;  
GO  
  
SELECT * FROM Production.NewLocation ;  
GO  
```  
  
### <a name="f-granting-permission-to-execute-next-value-for"></a>F. NEXT VALUE FOR を実行する権限を付与する  
 次の例では付与**更新**という名前のユーザーの権限を`AdventureWorks\Larry`を実行する権限`NEXT VALUE FOR`を使用して、`Test.CounterSeq`シーケンス。  
  
```  
GRANT UPDATE ON OBJECT::Test.CounterSeq TO [AdventureWorks\Larry] ;  
```  
  
## <a name="see-also"></a>参照  
 [SEQUENCE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

