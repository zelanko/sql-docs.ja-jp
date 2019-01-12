---
title: sp_bindrule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindrule_TSQL
- sp_bindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindrule
ms.assetid: 2606073e-c52f-498d-a923-5026b9d97e67
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d08f754022ae28cfce074978bfdd8c3f79ba71a6
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54128412"
---
# <a name="spbindrule-transact-sql"></a>sp_bindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ルールを列または別名データ型にバインドします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 使用[Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md)代わりにします。 チェックのキーワードを使用して制約を作成するかを確認、[テーブルの作成](../../t-sql/statements/create-table-transact-sql.md)または[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)ステートメントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_bindrule [ @rulename = ] 'rule' ,   
     [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@rulename=**] **'**_ルール_**'**  
 CREATE RULE ステートメントによって作成されたルールの名前です。 *ルール*、 **nvarchar(776)** の既定値はありません。  
  
 [  **@objname=**] **'**_object_name_**'**  
 ルールがバインドされるテーブルと列、または別名データ型です。 **text**、**ntext**、**image**、**varchar(max)**、**nvarchar(max)**、**varbinary(max)**、**xml**、CLR ユーザー定義型、**timestamp** の列には、ルールをバインドできません。 また、計算列にもバインドできません。  
  
 *object_name*は**nvarchar (776)** 既定値はありません。 場合*object_name*は 1 つの要素名では、別名データ型として解決されます。 2 部構成または 3 部構成の名前の場合は、最初にテーブルおよび列として解決されます。この解決が失敗すると、別名データ型として解決されます。 既存の別名データ型の列を継承する既定では、*ルール*ルールを直接その列にバインドしない限り、します。  
  
> [!NOTE]  
>  *object_name* 、角かっこを含めることができます **[** と **]** 文字で区切られた識別子の文字として。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
> [!NOTE]  
>  別名データ型を使用する式に対して作成されたルールは、列または別名データ型にバインドできますが、参照されてもコンパイルできません。 別名データ型に対して作成されたルールは使用しないでください。  
  
 [  **@futureonly=** ] **'**_futureonly_flag_**'**  
 ルールを別名データ型にバインドするときにのみ使用されます。 *future_only_flag*は**varchar (15)** 既定値は NULL です。 このパラメーターを設定すると**futureonly**エイリアス データ型の既存の列を新しいルールを継承しないようにします。 場合*futureonly_flag*が null の場合、新しいルールを現在ルールがあるいないか、別名データ型の既存のルールを使用している別名データ型の列にバインドされます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 (ただし、CHECK 制約を使用することを推奨)、新しいルールを列にバインドすることができます、別名データ型にする、または**sp_bindrule**せず、既存のルールをバインド解除します。 元のルールはオーバーライドされます。 既に CHECK 制約のある列にルールをバインドすると、すべての制限が評価されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にはルールをバインドできません。  
  
 ルールは、バインド時ではなく INSERT ステートメントを試行したときに設定されます。 列に文字のルールをバインドすることができます**数値**このような INSERT 操作は有効ではありませんが、データを入力します。  
  
 別名データ型の既存の列がない限り、新しい規則を継承*futureonly_flag*として指定されて**futureonly**します。 別名データ型が定義された新しい列は、常にルールを継承します。 しかし、ALTER TABLE ステートメントの ALTER COLUMN 句によって、列のデータ型をルールがバインドされた別名データ型に変更すると、データ型にバインドしているルールはその列に継承されません。 ルールする必要があります具体的には列にバインドするを使用して**sp_bindrule**します。  
  
 関連情報を追加する列にルールをバインドすると、 **sys.columns**テーブルです。 関連情報を追加するエイリアス データ型にルールをバインドすると、 **sys.types**テーブルです。  
  
## <a name="permissions"></a>アクセス許可  
 テーブル列にルールをバインドするには、そのテーブルに対する ALTER 権限が必要です。 別名データ型にルールをバインドするには、その別名データ型に対する CONTROL 権限、またはそのデータ型の属するスキーマに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-binding-a-rule-to-a-column"></a>A. 列にルールをバインドする  
 CREATE RULE ステートメントを使用して `today` という名前のルールが現在のデータベースで作成されているものとします。次の例では、`HireDate` テーブルの `Employee` 列に、このルールをバインドします。 行が `Employee` テーブルに追加されると、`HireDate` 列のデータは `today` ルールと照らし合わせてチェックされます。  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-rule-to-an-alias-data-type"></a>B. 別名データ型にルールをバインドする  
 `rule_ssn` という名前のルールがあり、`ssn` という名前の別名データ型があるものとします。次の例では、`rule_ssn` を `ssn` にバインドします。 CREATE TABLE ステートメントで、`ssn` 型の列は `rule_ssn` ルールを継承します。 型の既存の列`ssn`も継承、`rule_ssn`ルールは、しない限り、 **futureonly**が指定されて*futureonly_flag*、または`ssn`に直接バインドされたルールがあります。 列にバインドされているルールは、データ型にバインドされているルールより常に優先します。  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'rule_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>C. futureonly_flag を使用する  
 次の例では、`rule_ssn` ルールを別名データ型 `ssn` にバインドします。 `futureonly` が指定されているため、`ssn` 型の既存の列は影響を受けません。  
  
```  
USE master;  
GO  
EXEC sp_bindrule rule_ssn, 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. 区切られた識別子を使用する  
 次の例で区切られた識別子の使用を示しています。 *object_name*パラメーター。  
  
```  
USE master;  
GO  
CREATE TABLE [t.2] (c1 int) ;  
-- Notice the period as part of the table name.  
EXEC sp_bindrule rule1, '[t.2].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [DROP RULE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
