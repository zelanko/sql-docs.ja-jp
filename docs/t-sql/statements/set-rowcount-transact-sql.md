---
title: "SET ROWCOUNT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_ROWCOUNT_TSQL
- ROWCOUNT_TSQL
- SET ROWCOUNT
- ROWCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- row return limitations [SQL Server]
- SET ROWCOUNT statement
- number of rows affected by statement
- ROWCOUNT option
- counting rows
- stopping queries
- limiting rows returned
- queries [SQL Server], stopping
ms.assetid: c6966fb7-6421-47ef-98f3-82351f2f6bdc
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eda7f9faf2bb45b06cf1112dbe48cbdb281fdab3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-rowcount-transact-sql"></a>SET ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  により[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定数の行が返された後、クエリの処理を停止します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SET ROWCOUNT { number | @number_var }   
```  
  
## <a name="arguments"></a>引数  
 *数*| @*number_var*  
 特定のクエリを停止するまでに処理される行数を整数で指定します。  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  SQL Server の将来のリリースでは、SET ROWCOUNT を使用しても、DELETE、INSERT、および UPDATE ステートメントが影響を受けることはありません。 新しい開発作業で、DELETE、INSERT、および UPDATE ステートメントで SET ROWCOUNT の使用を避けるため、現在それを使用するアプリケーションの変更を検討してください。 同様の処理を行う場合は、TOP 構文を使用します。 詳細については、次を参照してください。 [TOP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
 このオプションを off に設定して、すべての行が返されるように、するには、SET ROWCOUNT 0 を指定します。  
  
 SET ROWCOUNT オプションを設定すると、大部分の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、指定した行数の処理が終わったところで処理が停止します。 これにはトリガーも含まれます。 ROWCOUNT オプションは動的カーソルには影響しませんが、このオプションによってキーセット カーソルと非反映型カーソルの行セットは制限されます。 このオプションの使用には注意が必要です。  
  
 SET ROWCOUNT で指定された行数が SELECT ステートメントの TOP キーワードの値より少ない場合は、SET ROWCOUNT の値が優先されます。  
  
 SET ROWCOUNT は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 SET ROWCOUNT を指定した場合、指定した数の行が返されると処理は停止します。 次の例では、500 行での条件を満たすことに注意してください`Quantity`より小さい`300`です。 SET ROWCOUNT の適用後、すべての行が返されたわけではないことがわかります。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT count(*) AS Count  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Count`  
  
 `-----------`  
  
 `537`  
  
 `(1 row(s) affected)`  
  
 これで、設定`ROWCOUNT`に`4`し 4 行だけが返されることを示すためにすべての行を返します。  
  
```  
SET ROWCOUNT 4;  
SELECT *  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 `(4 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 SET ROWCOUNT を指定した場合、指定した数の行が返されると処理は停止します。 次の例では、20 を超える行がの条件を満たすことに注意してください`AccountType = 'Assets'`です。 SET ROWCOUNT の適用後、すべての行が返されたわけではないことがわかります。  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 5;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
 すべての行を返すには、行カウントを 0 に設定します。  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 0;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


