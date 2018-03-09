---
title: "スラッシュ スター (ブロック コメント) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2017
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
- /*...*/_TSQL
- Comment
- /*...*/
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- /*...*/ (comment)
- remarks [SQL Server]
- comments [SQL Server]
ms.assetid: 4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4d7181070cb0524b31364a915040307198054780
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="slash-star-block-comment-transact-sql"></a>スラッシュ スター (ブロック コメント) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]


  ユーザーが入力したテキストを示します。 テキストの間、/* と\*サーバーによっては評価されません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
/*  
text_of_comment  
*/  
```  
  
## <a name="arguments"></a>引数  
 *text_of_comment*  
 コメントのテキストです。 1 つ以上の文字列です。  
  
## <a name="remarks"></a>解説  
 コメントは、単独行に指定したり、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの中に指定できます。 によって複数行のコメントを示す必要があります/* と\*/です。 複数行のコメントの多くの場合に使用されるスタイルの規則は、最初の行を開始する/\*後続の行は\*\*で終わります\*/です。  
  
 コメントの長さには制限がありません。  
  
 入れ子になったコメントを使用できます。 場合、/* 文字パターンが既存のコメント内に任意の場所は入れ子になったコメントの始まりとして処理され、そのため、終了が必要です\*コメント マーク/です。 終了のコメント マークが存在しない場合は、エラーが生成されます。  
  
 たとえば、次のコードではエラーが生成されます。  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/   
SELECT @@VERSION;  
GO   
```  
  
 このエラーを回避するには、次のように変更してください。  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/ */  
SELECT @@VERSION;  
GO  
  
```  
  
## <a name="examples"></a>使用例  
 次の例では、コード セクションの作業内容を説明するコメントを使用しています。  
  
```  
USE AdventureWorks2012;  
GO  
/*  
This section of the code joins the Person table with the Address table,   
by using the Employee and BusinessEntityAddress tables in the middle to   
get a list of all the employees in the AdventureWorks2012 database   
and their contact information.  
*/  
SELECT p.FirstName, p.LastName, a.AddressLine1, a.AddressLine2, a.City, a.PostalCode  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e ON p.BusinessEntityID = e.BusinessEntityID   
JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
JOIN Person.Address AS a ON ea.AddressID = a.AddressID;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [--&#40;です。コメント &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/comment-transact-sql.md)   
 [フロー制御言語 &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)  
  
  

