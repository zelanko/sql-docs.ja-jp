---
title: "UPDATE() (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE()_TSQL
- UPDATE()
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], UPDATE function
- testing column updates
- UPDATE function
- UPDATE() function
- detecting changes
- columns [SQL Server], change detection
- UPDATE statement [SQL Server], UPDATE function
- verifying column updates
- checking column updates
ms.assetid: 8e3be25b-2e3b-4d1f-a610-dcbbd8d72084
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 644848af581b0db5a26b9958db4660b4cab66163
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="update---trigger-functions-transact-sql"></a>更新プログラム - トリガー関数 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  テーブルまたはビューの指定された列で、INSERT または UPDATE が行われたかどうかを示すブール値を返します。 UPDATE() は [!INCLUDE[tsql](../../includes/tsql-md.md)] の INSERT または UPDATE トリガーの内部のどこでも使用でき、そのトリガーが特定の動作を実行すべきかどうかをテストすることができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATE ( column )   
```  
  
## <a name="arguments"></a>引数  
 *列*  
 INSERT 動作または UPDATE 動作をテストする列の名前です。 トリガーの ON 句にテーブル名が指定されているため、列名の前にテーブル名を含めないでください。 任意の列を指定できます[データ型](../../t-sql/data-types/data-types-transact-sql.md)でサポートされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ただし、計算列を使用することはできません。  
  
## <a name="return-types"></a>戻り値の型  
 ブール値  
  
## <a name="remarks"></a>解説  
 INSERT または UPDATE が成功するかどうかにかかわらず、UPDATE() は TRUE を返します。  
  
 1 つ以上の列の挿入または更新操作をテストする別個の更新プログラムを指定します (*列*) 次の 1 つ目の句。 COLUMNS_UPDATED を使用しても、複数の列で INSERT 動作または UPDATE 動作をテストできます。 これは、挿入または更新された列を示すビット パターンを返します。  
  
 INSERT 動作では、列には明示的な値または暗黙的な (NULL) 値が挿入されるので、IF UPDATE は TRUE の値を返します。  
  
> [!NOTE]  
>  IF UPDATE (*列*n) 場合、IF と同じ句機能しています.それ以外の場合、または WHILE 句および使用を開始しています.終了ブロック。 詳細については、次を参照してください。[フロー制御言語 & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md).  
  
 更新 (*列*) 内部のどこでも使用できる、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガーします。  
  
## <a name="examples"></a>使用例  
 次の例では、`StateProvinceID` テーブルの `PostalCode` 列または `Address` 列を更新しようとするときにクライアントへのメッセージを出力する、トリガーを作成します。  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
      WHERE name = 'reminder' AND type = 'TR')  
   DROP TRIGGER Person.reminder;  
GO  
CREATE TRIGGER reminder  
ON Person.Address  
AFTER UPDATE   
AS   
IF ( UPDATE (StateProvinceID) OR UPDATE (PostalCode) )  
BEGIN  
RAISERROR (50009, 16, 10)  
END;  
GO  
-- Test the trigger.  
UPDATE Person.Address  
SET PostalCode = 99999  
WHERE PostalCode = '12345';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [COLUMNS_UPDATED と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  

