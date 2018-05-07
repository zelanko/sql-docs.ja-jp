---
title: sp_unbindrule (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_unbindrule_TSQL
- sp_unbindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindrule
ms.assetid: f54ee155-c3c9-4f1a-952e-632a8339f0cc
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: be14a4885cea481edda6ba7465ac2c5aa969ec1b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spunbindrule-transact-sql"></a>sp_unbindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内の列または別名データ型のルールをバインド解除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] DEFAULT キーワードを使用して既定の定義を作成することをお勧め、 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)ステートメント代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_unbindrule [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@objname=** ] **'***object_name***'**  
 ルールをバインド解除する、テーブルと列、または別名データ型の名前を指定します。 *object_name*は**nvarchar (776)**、既定値はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、最初に列名に対して、次に別名データ型に対して、2 つの要素で構成される識別子の解決が試行されます。 別名データ型のルールをバインド解除すると、指定したデータ型の列のルールがすべてバインド解除されます。 ただし、同じデータ型でも、ルールが直接バインドされている列には影響はありません。  
  
> [!NOTE]  
>  *object_name*角かっこを含めることができます **:operator[]** として識別子の区切り文字。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
 [ **@futureonly=** ] **'***futureonly_flag***'**  
 別名データ型からルールをバインド解除する場合にのみ使用します。 *futureonly_flag*は**varchar (15)**、既定値は NULL です。 ときに*futureonly_flag*は**futureonly**、そのデータ型の既存の列には、指定されたルールは失われません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 ルールのテキストを表示するには、ルール名をパラメーターに使用して **sp_helptext** を実行します。  
  
 ルールがバインド解除、バインドに関する情報はから削除、 **sys.columns**テーブルの列との間に、ルールがバインドされていた場合、 **sys.types**テーブルの場合は、ルールを別名データ型にバインドされました。  
  
 別名データ型からルールをバインド解除すると、その別名データ型のすべての列からも該当するルールがバインド解除されます。 ルールは、列のデータ型が変更されたか後で ALTER TABLE ステートメントの ALTER COLUMN 句にもバインド可能性がありますを使用してこれらの列からルールをバインド解除する必要があります具体的には**sp_unbindrule**を指定して、列の名前。  
  
## <a name="permissions"></a>権限  
 テーブル列からルールをバインド解除するには、そのテーブルに対する ALTER 権限が必要です。 別名データ型からルールをバインド解除するには、そのデータ型に対する CONTROL 権限、またはそのデータ型が属するスキーマに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-unbinding-a-rule-from-a-column"></a>A. 列のルールをバインド解除する  
 次の例からルールをバインド解除、`startdate`の列、`employees`テーブル。  
  
```  
EXEC sp_unbindrule 'employees.startdate';  
```  
  
### <a name="b-unbinding-a-rule-from-an-alias-data-type"></a>B. 別名データ型からルールをバインド解除する  
 次の例では、別名データ型 `ssn` からルールをバインド解除します。 これには、現在および将来の型の列からルールがバインド解除します。  
  
```  
EXEC sp_unbindrule ssn;  
```  
  
### <a name="c-using-futureonlyflag"></a>C. Futureonly_flag を使用します。  
 次の例では、既存の `ssn` 列に影響を与えずに、別名データ型 `ssn` からルールをバインド解除します。  
  
```  
EXEC sp_unbindrule 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. 区切られた識別子を使用する  
 次の例で区切られた識別子を使用して、 *object_name*パラメーター。  
  
```  
CREATE TABLE [t.4] (c1 int); -- Notice the period as part of the table   
-- name.  
GO  
CREATE RULE rule2 AS @value > 100;  
GO  
EXEC sp_bindrule rule2, '[t.4].c1' -- The object contains two   
-- periods; the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
GO  
EXEC sp_unbindrule '[t.4].c1';  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [DROP RULE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
