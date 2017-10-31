---
title: "rowversion (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- timestamp_TSQL
- timestamp
dev_langs:
- TSQL
helpviewer_keywords:
- rowversion data type
- size [SQL Server], rowversion
- row version-stamping [SQL Server]
- rowversion columns
- version-stamping table rows
- unique rowversion numbers
- unique timestamp numbers
- timestamp data type
- timestamp columns
- size [SQL Server], timestamp
ms.assetid: 65c9cf0e-3e8a-45f8-87b3-3460d96afb0b
caps.latest.revision: 57
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47bcf3007657c1cf8f77c364aa21839cdd27d1ba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

データベース内で自動的に生成され、一意の 2 進数を公開するデータ型です。 **rowversion**は通常、テーブルの行のバージョン指定のメカニズムとして使用します。 記憶領域のサイズは 8 バイトです。 **Rowversion**データ型は、増分する番号だけであり、日付または時刻では保持されません。 録音するには、日付または時刻を使用して、 **datetime2**データ型。
  
## <a name="remarks"></a>解説  
各データベースを含むテーブルに対して実行される update 操作または挿入ごとにインクリメントされるカウンターには、 **rowversion**データベース内の列です。 このカウンターは、データベース rowversion です。 このカウンターは、時計に関連付けられる実際の時刻ではなく、データベース内の相対的な時間を追跡します。 テーブルには、1 つだけ持つことができます**rowversion**列です。 たびを持つ行、 **rowversion** 、増加したデータベース rowversion 値が挿入で、列が変更または挿入、 **rowversion**列です。 このプロパティにより、 **rowversion**列、不適切なキー、特に主キー。 行を更新すると rowversion 値が変わるので、キーの値も変わります。 列が主キー内にある場合、以前のキーの値は無効になり、この以前の値を参照する外部キーも無効になります。 動的カーソルでテーブルを参照する場合、すべての更新操作はカーソル上の行の位置を変更します。 列がインデックス キー内にある場合、データ行を更新すると、インデックスも更新されます。  **Rowversion**行の値が変更されていない場合でも、update ステートメントと値が増加します。 (たとえば、列の値が 5、update ステートメント、値を 5 に設定する場合は、この操作と見なされます更新、変更がない場合でも、 **rowversion**がインクリメントされます)。
  
**タイムスタンプ**のシノニムには、 **rowversion**データを入力し、動作が適用のデータ型のシノニムです。 DDL ステートメントで使用して**rowversion**の代わりに**タイムスタンプ**可能な限りです。 詳細については、次を参照してください。[データ型のシノニムと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] **タイムスタンプ**データ型が異なる、**タイムスタンプ**ISO 規格で定義されているデータ型。
  
> [!NOTE]  
>  **タイムスタンプ**構文は推奨されません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
CREATE TABLE または ALTER TABLE ステートメントでは列名を指定する必要はありません、**タイムスタンプ**データ型の例を示します。
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
列名が指定されていない場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]が生成されます、**タイムスタンプ**列の名前です。 ただし、、 **rowversion**シノニムがこの動作に従っていません。 使用すると**rowversion**、たとえば、列名を指定する必要があります。
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  重複して**rowversion**を SELECT INTO ステートメントを使用して値を生成することができます、 **rowversion**列が SELECT リストに存在します。 使用しないで**rowversion**をこのようにします。  
  
Null 値非許容**rowversion**列は同じ意味、 **binary (8)**列です。 Null 許容型**rowversion**列は同じ意味、 **varbinary (8)**列です。
  
使用することができます、 **rowversion**簡単に行を update ステートメントがあるかどうかを決定する行の列が前回読み取られて以降に対して実行します。 Update ステートメントが行に対してが実行された場合、rowversion 値が更新されます。 場合は、行に対して update ステートメントでが実行されませんでした、rowversion 値は前回の読み取り時と同じです。 データベースの現在の rowversion 値を返すには使用[@@DBTS](../../t-sql/functions/dbts-transact-sql.md)です。
  
追加することができます、 **rowversion**列を複数のユーザーが同時に行を更新するときに、データベースの整合性を維持するためにテーブルにします。 テーブルに対するクエリを再度実行せずに、行数や更新された行を把握する必要がある場合もあります。
  
たとえば、`MyTest` という名前のテーブルを作成するとします。 以下を実行して、テーブルにデータを設定する[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。
  
```sql
CREATE TABLE MyTest (myKey int PRIMARY KEY  
    ,myValue int, RV rowversion);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (2, 0);  
GO  
```  
  
次に、以下のサンプル [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、更新中に `MyTest` テーブルにオプティミスティック同時実行制御を実装します。
  
```sql
DECLARE @t TABLE (myKey int);  
UPDATE MyTest  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND RV = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
`myValue`**rowversion**を最後に、行を読み取ることを示す行の列の値。 実際、この値を置き換える必要があります**rowversion**値。 実際の使用例**rowversion**値は、0x00000000000007d3 などになります。
  
サンプルを追加することもできます。[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントをトランザクションにします。 トランザクションの範囲内で `@t` 変数に対してクエリを実行すると、`myKey` テーブルに対するクエリを再度実行しなくても、テーブルの更新済みの `MyTes` 列を取得できます。
  
同じ例を次に示しますを使用して、**タイムスタンプ**構文。
  
```sql
CREATE TABLE MyTest2 (myKey int PRIMARY KEY  
    ,myValue int, TS timestamp);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (2, 0);  
GO  
DECLARE @t TABLE (myKey int);  
UPDATE MyTest2  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND TS = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)
  
  

