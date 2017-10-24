---
title: "既定値 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_DEFAULT_TSQL
- CREATE DEFAULT
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], default
- default objects
- CREATE DEFAULT statement
- objects [SQL Server], creating
- DEFAULT definition
ms.assetid: 08475db4-7d90-486a-814c-01a99d783d41
caps.latest.revision: 47
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71c0f964d245be92fb8d2be19e074fbd34dd616e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-default-transact-sql"></a>CREATE DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  デフォルトと呼ばれるオブジェクトを作成します。 デフォルト (既定値) は、列または別名データ型にバインドされると、明示的な指定がない場合にオブジェクトのバインド先の列 (別名データ型の場合はすべての列) に挿入される値を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、ALTER TABLE または CREATE TABLE の DEFAULT キーワードを使用して作成された既定の定義を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE DEFAULT [ schema_name . ] default_name   
AS constant_expression [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 デフォルトが所属するスキーマの名前を指定します。  
  
 *default_name*  
 デフォルトの名前です。 既定の名前がの規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 デフォルトの所有者名の指定は省略可能です。  
  
 *constant_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)(すべての列またはその他のデータベース オブジェクトの名前を含めることはできません) のみの定数の値を含むです。 別名データ型を含んでいるものを除き、任意の定数、組み込み関数、または計算式を使用できます。 ユーザー定義関数は使用できません。 文字および日付定数を単一引用符で囲みます (**'**); 金額、整数および浮動小数点定数は必要ありません引用符。 binary 型データには先頭に 0x を、金額には先頭に円記号 (\) を指定します。 既定値と列のデータ型には互換性があることが必要です。  
  
## <a name="remarks"></a>解説  
 デフォルト名は現在のデータベース内でのみ作成できます。 データベース内では、デフォルトの名前はスキーマごとに一意であることが必要です。 既定値を作成すると、使用して**sp_bindefault**列または別名データ型にバインドします。  
  
 既定値は、バインド先の列と互換性がない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定値を挿入しようとするときにエラー メッセージを生成します。 たとえば、N/A の既定値として使用できません、**数値**列です。  
  
 バインドしてある列より既定値が長い場合、値は切り捨てられます。  
  
 CREATE DEFAULT ステートメントは、その他と組み合わせることはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]1 つのバッチ内のステートメント。  
  
 同じ名前の新しい 1 つを作成する前に、既定値を削除する必要があり、実行する、既定のバインドを解除する必要があります**sp_unbindefault**が削除される前にします。  
  
 列が既定値とそれに関連するルールの両方を持つ場合、既定値はそのルールに従っている必要があります。 ルールに矛盾するデフォルトは挿入できません。挿入を試行すると、そのたびに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではエラー メッセージが表示されます。  
  
 列にバインドされているとき、既定値は次の場合に挿入されます。  
  
-   値が明示的に挿入されていない場合。  
  
-   DEFAULT VALUES キーワードまたは DEFAULT キーワードを INSERT と組み合わせて使用し、既定値を挿入した場合。  
  
 列の作成時に NOT NULL が指定されていて、その列のデフォルトが作成されていない場合は、ユーザーによってその列にエントリが入力されないとエラー メッセージが表示されます。 次の表は、デフォルトの有無と、NULL または NOT NULL として定義された列の関係を示しています。 表中の各エントリは結果を示しています。  
  
|列の定義|入力なし、デフォルトなし|入力なし、デフォルトあり|NULL を入力、デフォルトなし|NULL を入力、デフォルトあり|  
|-----------------------|--------------------------|-----------------------|----------------------------|-------------------------|  
|**NULL**|NULL|既定値 (default)|NULL|NULL|  
|**NOT NULL**|[エラー]|既定値 (default)|error|error|  
  
 既定の名前を変更するには使用**sp_rename**です。 既定でレポートを**sp_help**です。  
  
## <a name="permissions"></a>Permissions  
 CREATE DEFAULT を実行するには、ユーザーは少なくとも現在のデータベース内では CREATE DEFAULT 権限を、デフォルトが作成されるスキーマに対しては ALTER 権限を持つ必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-simple-character-default"></a>A. 単純な文字のデフォルトを作成する  
 次の例では、"`unknown`" という文字のデフォルトを作成します。  
  
```tsql  
USE AdventureWorks2012;  
GO  
CREATE DEFAULT phonedflt AS 'unknown';  
```  
  
### <a name="b-binding-a-default"></a>B. デフォルトをバインドする  
 次の例は、例 A で作成したデフォルトをバインドします。既定値のエントリが指定されていない場合にのみ有効になります、`Phone`の列、`Contact`テーブル。 エントリの省略は、INSERT ステートメントで NULL を明示的に指定する場合とは異なることに注意してください。  
  
 既定の名前付きため`phonedflt`が存在しない次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは失敗します。 次の例は、説明用のものです。  
  
```tsql  
USE AdventureWorks2012;  
GO  
sp_bindefault 'phonedflt', 'Person.PersonPhone.PhoneNumber';  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [既定値 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-default-transact-sql.md)   
 [DROP RULE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-rule-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [sp_bindefault & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  

