---
title: "SET STATISTICS TIME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_TIME_TSQL
- SET STATISTICS TIME
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], statement processing
- time [SQL Server], statement processing statistics
- SET STATISTICS TIME statement
- STATISTICS TIME option
- statements [SQL Server], statistical information
- parsing [SQL Server], SET STATISTICS TIME statement
- compile times [SQL Server]
- execution processing time [SQL Server]
ms.assetid: eec2e1cd-a29d-4cf3-a271-be9d61506f15
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: acd4684ea6b44f3a7371424eb6c90305e78841fc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-statistics-time-transact-sql"></a>SET STATISTICS TIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  各ステートメントの解析、コンパイル、および実行に必要な時間をミリ秒単位で表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET STATISTICS TIME { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 SET STATISTICS TIME が ON の場合、ステートメントの処理時間の統計が表示されます。 OFF の場合、時間の統計は表示されません。  
  
 SET STATISTICS TIME は、解析時ではなく実行時に設定されます。  
  
 Microsoft[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を有効にしたときに起動されるファイバー モードで正確な統計情報を提供するようになって、**簡易プーリング**構成オプション。  
  
 **Cpu**内の列、 **sysprocesses** SET STATISTICS TIME が ON でクエリの実行時にのみ、テーブルが更新されます。 SET STATISTICS TIME が OFF の場合、 **0**が返されます。  
  
 この設定が ON であるか OFF であるかによって、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [現在の利用状況] の [プロセス情報] ビューにある CPU 列にも影響します。  
  
## <a name="permissions"></a>Permissions  
 SET STATISTICS TIME を使用するユーザーを実行する適切なアクセス許可が必要、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 SHOWPLAN 権限は必要ありません。  
  
## <a name="examples"></a>使用例  
 次の例では、サーバーの実行、解析、コンパイルの時間を表示します。  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS TIME ON;  
GO  
SELECT ProductID, StartDate, EndDate, StandardCost   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS TIME OFF;  
GO  
```  
  
 Here is the result set:  
  
```  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
  
(269 row(s) affected)  
  
SQL Server Execution Times:  
   CPU time = 0 ms,  elapsed time = 2 ms.  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET STATISTICS IO & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statistics-io-transact-sql.md)  
  
  

