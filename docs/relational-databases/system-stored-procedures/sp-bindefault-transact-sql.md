---
title: "sp_bindefault (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/25/2015
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
- sp_bindefault
- sp_bindefault_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindefault
ms.assetid: 3da70c10-68d0-4c16-94a5-9e84c4a520f6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3e23435d6c0a2db3809722856b9daa6b2d66505
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spbindefault-transact-sql"></a>sp_bindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  デフォルトを列または別名データ型にバインドします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]DEFAULT キーワードを使用して既定の定義を作成することをお勧め、 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)ステートメント代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_bindefault [ @defname = ] 'default' ,   
    [ @objname = ] 'object_name'   
    [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@defname=** ] **'***既定***'**  
 CREATE DEFAULT で作成されるデフォルトの名前です。 *既定*は**nvarchar (776)**、既定値はありません。  
  
 [  **@objname=** ] **'***object_name***'**  
 デフォルトがバインドされるテーブルと列、または別名データ型の名前です。 *object_name*は**nvarchar (776)**既定値はありません。 *object_name*を定義することはできません、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、または CLRユーザー定義型です。  
  
 場合*object_name* 1 部構成の名前は、別名データ型として解決されます。 2 部構成または 3 部構成の名前の場合は、最初にテーブルおよび列として解決され、この解決が失敗すると、別名データ型として解決されます。 既定では、別名データ型の既存の列を継承*既定*既定値を直接その列にバインドしない限り、します。 既定値をバインドできません、**テキスト**、 **ntext**、**イメージ**、 **varchar (max)**、 **nvarchar (max)**、**varbinary (max)**、 **xml**、**タイムスタンプ**、または CLR ユーザー定義型列、IDENTITY プロパティを持つ列、計算列または列を既定の制約を既に持っています。  
  
> [!NOTE]  
>  *object_name*角かっこを含めることができます**:operator[]**区切られた識別子として。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
 [  **@futureonly=** ] **'***futureonly_flag***'**  
 デフォルトを別名データ型にバインドするときにのみ使用されます。 *futureonly_flag*は**varchar (15)**既定値は NULL です。 このパラメーターに設定すると**futureonly**、そのデータ型の既存の列は、新しいデフォルトを継承できません。 デフォルトを列にバインドするときには決してこのパラメーターを使用しないでください。 場合*futureonly_flag*が NULL の場合、新しいデフォルトは現在あるありません既定か、別名データ型の既存のデフォルトを使用している別名データ型の列にバインドします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 使用することができます**sp_bindefault**デフォルトをバインドする新しい列を使用して、既定の制約、または別名データ型に、既存のデフォルトをアンバインドせずにします。 既存のデフォルトは無効になります。 デフォルトをバインドすることはできません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型または CLR ユーザー定義型です。 既定値はするがバインドされている、列と互換性がない場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]にバインドするときではなく、既定値を挿入しようとするときにエラー メッセージを返します。  
  
 既定のいずれかがそれらに直接バインドしない限り、別名データ型の既存の列が、新しいデフォルトを継承または*futureonly_flag*として指定された**futureonly**です。 別名データ型の新しい列は常にデフォルトを継承します。  
  
 関連する情報を追加の列にデフォルトをバインドするときに、 **sys.columns**カタログ ビューです。 関連する情報を追加、別名データ型にデフォルトをバインドするときに、 **sys.types**カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 ユーザーが、テーブルを所有またはのメンバーである必要があります、 **sysadmin**固定サーバー ロール、または**db_owner**と**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-binding-a-default-to-a-column"></a>A. 列にデフォルトをバインドする  
 既定の名前付き`today`に既定の CREATE DEFAULT、次の例のバインドを使用して、現在のデータベースで定義されて、`HireDate`の列、`Employee`テーブル。 `Employee` テーブルに行を追加するときに、`HireDate` 列の入力がなければ、この列にデフォルト `today` が入力されます。  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-default-to-an-alias-data-type"></a>B. 別名データ型にデフォルトをバインドする  
 `def_ssn` という名前のデフォルトと、`ssn` という別名データ型が既に存在しています。 次の例は、既定値を連結`def_ssn`に`ssn`です。 既定値は、別名データ型が割り当てられているすべての列によって継承されているテーブルが作成されると、`ssn`です。 既存の型の列**ssn**デフォルトを継承も**def_ssn**がない限り、 **futureonly**が指定されて*futureonly_flag*値または、列のデフォルトが直接バインドしない限り、します。 列にバインドされているデフォルトは、データ型にバインドされているデフォルトより常に優先します。  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>C. futureonly_flag を使用する  
 次の例は、既定値を連結`def_ssn`、別名データ型に`ssn`です。 **Futureonly**が指定されている型の既存の列`ssn`が影響を受けます。  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. 区切られた識別子を使用する  
 次の例は、区切られた識別子を使用して`[t.1]`の*object_name*です。  
  
```  
USE master;  
GO  
CREATE TABLE [t.1] (c1 int);   
-- Notice the period as part of the table name.  
EXEC sp_bindefault 'default1', '[t.1].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name,   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [既定値 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_unbindefault &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
