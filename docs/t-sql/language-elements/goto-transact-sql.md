---
title: "GOTO (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GOTO
- GOTO_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- skipping statements
- Transact-SQL statements, skipping
- labels [SQL Server]
- statements [SQL Server], skipping
- GOTO statement
ms.assetid: 589b6f8e-dc80-416f-9e74-48bed5337f58
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c5614843f961d1ff3188ba1f3caa589d77c4735
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="goto-transact-sql"></a>GOTO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  実行の流れを指定のラベルに分岐します。 [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたは GOTO の後のステートメントはスキップされ、ラベルから処理を続行します。 GOTO ステートメントとラベルは、プロシージャ、バッチ、またはステートメント ブロック内のどこででも使用できます。 GOTO ステートメントは入れ子にすることができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
Define the label:   
label:   
Alter the execution:  
GOTO label   
```  
  
## <a name="arguments"></a>引数  
 *ラベル*  
 GOTO によりラベルを指定した場合、そのラベルが以降の処理を開始する位置になります。 ラベルの規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 GOTO の使用の有無にかかわらず、ラベルをコメント行として使用することができます。  
  
## <a name="remarks"></a>解説  
 GOTO は、条件付きフロー制御ステートメント、ステートメント ブロック、またはプロシージャ内に存在できますが、バッチの外にあるラベルに移動できません。 GOTO による分岐は、GOTO の前後に定義されたラベルに移動できます。  
  
## <a name="permissions"></a>Permissions  
 GOTO 権限は、特に指定のない限りすべての有効なユーザーに与えられます。  
  
## <a name="examples"></a>使用例  
 次の例では、`GOTO` を分岐手段として使用する方法を示します。  
  
```  
DECLARE @Counter int;  
SET @Counter = 1;  
WHILE @Counter < 10  
BEGIN   
    SELECT @Counter  
    SET @Counter = @Counter + 1  
    IF @Counter = 4 GOTO Branch_One --Jumps to the first branch.  
    IF @Counter = 5 GOTO Branch_Two  --This will never execute.  
END  
Branch_One:  
    SELECT 'Jumping To Branch One.'  
    GOTO Branch_Three; --This will prevent Branch_Two from executing.  
Branch_Two:  
    SELECT 'Jumping To Branch Two.'  
Branch_Three:  
    SELECT 'Jumping To Branch Three.';  
```  
  
## <a name="see-also"></a>参照  
 [フロー制御言語 & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)   
 [作業を開始してください.END & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [中断 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/break-transact-sql.md)   
 [続行 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/continue-transact-sql.md)   
 [もし。。。ELSE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WAITFOR & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/waitfor-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  

