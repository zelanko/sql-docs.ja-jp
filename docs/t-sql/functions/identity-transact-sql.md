---
title: "@@IDENTITY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IDENTITY_TSQL'
- '@@IDENTITY'
dev_langs:
- TSQL
helpviewer_keywords:
- last-inserted identity values
- identity values [SQL Server], last-inserted
- '@@IDENTITY function'
ms.assetid: 912e4485-683c-41c2-97b3-8831c0289ee4
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 88cdaa1362e5d60b0f880c66c7fb7038ddb9f126
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40identity-transact-sql"></a>&#x40;&#x40; です識別情報 (TRANSACT-SQL)。
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  最後に挿入された ID 値を返すシステム関数です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@IDENTITY  
```  
  
## <a name="return-types"></a>戻り値の型  
 **numeric(38,0)**  
  
## <a name="remarks"></a>解説  
 INSERT、SELECT INTO、または一括コピー ステートメントが完了、@@IDENTITYステートメントによって生成される最後の id 値が含まれています。 かどうか、ステートメントがテーブルに影響しません、id 列を持つ@IDENTITYは NULL を返します。 複数の行を挿入すると場合、は、複数の id 値を生成する、@IDENTITY生成された最後の id 値を返します。 を呼び出す場合は、ステートメントでは、id 値を生成する挿入操作を実行する 1 つまたは複数のトリガーが起動、@IDENTITYステートメントが、トリガーによって生成された最後の id 値を返した直後後。 場合は、id 列をあるテーブルで挿入操作の実行後、トリガーが起動され、トリガー @ に id 列がない別のテーブルに挿入@IDENTITY最初の挿入の id 値を返します。 @@IDENTITY値が、トランザクションがロールバックされた場合、INSERT または SELECT INTO ステートメント、または一括コピーが失敗した場合、または前の設定に戻すことはできません。  
  
 失敗したステートメントとトランザクションによって、テーブルに対する現在の ID が変更され、ID 列値に差異が生じる可能性があります。 ID 値がロールバックされることはありません。これは、テーブルに値を挿入するトランザクションがコミットされない場合でも同じです。 たとえば、INSERT ステートメントが IGNORE_DUP_KEY 違反のために失敗しても、テーブルの現在の ID 値は増分されます。  
  
 @@IDENTITYSCOPE_IDENTITY、および IDENT_CURRENT は、類似した関数のテーブルの ID 列に挿入された最後の値を返すためです。  
  
 @@IDENTITY SCOPE_IDENTITY は、現在のセッションで任意のテーブルで生成された最後の id 値を返すとします。 ただし、SCOPE_IDENTITY が現在のスコープ内でのみ値を返します@@IDENTITYは、特定のスコープに限定されません。  
  
 IDENT_CURRENT はスコープとセッションには限定されませんが、特定のテーブルに限定されます。 IDENT_CURRENT は、任意のセッションとスコープの特定のテーブルに対して生成された ID 値を返します。 詳細については、次を参照してください。 [IDENT_CURRENT (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ident-current-transact-sql.md).  
  
 スコープ、@@IDENTITY関数は、現在のセッションを実行するローカル サーバーにします。 この関数は、リモート サーバーまたはリンク サーバーには適用できません。 別のサーバーで ID 値を取得するには、そのリモート サーバーまたはリンク サーバーでストアド プロシージャを実行し、(リモート サーバーまたはリンク サーバーのコンテキスト内で実行されている) そのストアド プロシージャが ID 値を収集し、ローカル サーバー上の呼び出し元の接続にこれを返すようにします。  
  
 レプリケーションが変わる可能性があります、@@IDENTITY値、レプリケーション トリガーやストアド プロシージャ内で使用されているためです。 @@IDENTITY列がレプリケーション アーティクルの一部である場合、最新のユーザーが作成した id の信頼性の高いインジケーターではありません。 構文を使用できます、SCOPE_IDENTITY() 関数の代わりに @@IDENTITYです。 詳細については、次を参照してください。 [SCOPE_IDENTITY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/scope-identity-transact-sql.md)  
  
> [!NOTE]  
>  呼び出し元のストアド プロシージャまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]を使用するステートメントを書き直す必要があります、`SCOPE_IDENTITY()`関数で、そのユーザーのステートメントのスコープ内で使用される最新の id とにより使用される入れ子になったトリガーのスコープ内の id ではなくを返しますレプリケーション。  
  
## <a name="examples"></a>使用例  
 次の例では、id 列を持つテーブルに行を挿入 (`LocationID`) を使用して`@@IDENTITY`を新しい行に使用する id 値を表示します。  
  
```  
USE AdventureWorks2012;  
GO  
--Display the value of LocationID in the last row in the table.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
INSERT INTO Production.Location (Name, CostRate, Availability, ModifiedDate)  
VALUES ('Damaged Goods', 5, 2.5, GETDATE());  
GO  
SELECT @@IDENTITY AS 'Identity';  
GO  
--Display the value of LocationID of the newly inserted row.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENT_CURRENT &#40;Transact-SQL&#41;](../../t-sql/functions/ident-current-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SCOPE_IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  

