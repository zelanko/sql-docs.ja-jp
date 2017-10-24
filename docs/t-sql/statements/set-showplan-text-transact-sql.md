---
title: "SET SHOWPLAN_TEXT (TRANSACT-SQL) |Microsoft ドキュメント"
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
- SHOWPLAN_TEXT
- SET_SHOWPLAN_TEXT_TSQL
- SET SHOWPLAN_TEXT
- SHOWPLAN_TEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- SET SHOWPLAN_TEXT statement
- canceling statement execution
- SHOWPLAN_TEXT option
- stopping statement execution
- estimated execution information [SQL Server]
ms.assetid: 2c4f3fc8-ff2c-4790-8b74-e7e8ef58f9a6
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7abd42acdcbfa4274686d3d8162e727cf36e5ee7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-showplantext-transact-sql"></a>SET SHOWPLAN_TEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行せず、 代わりに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメントの実行方法に関する詳細情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET SHOWPLAN_TEXT { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 SET SHOWPLAN_TEXT は、解析時ではなく実行時に設定されます。  
  
 SET SHOWPLAN_TEXT が ON の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ごとの実行情報を返します[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを実行することなしです。 返される情報は、このオプションが ON に設定されてから OFF に設定されるまでに発行されたすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントに関する実行プラン情報です。 たとえば、CREATE TABLE ステートメントが実行中に SET SHOWPLAN_TEXT が ON、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定したテーブルが存在しないユーザーに通知を同じテーブルに関連する後続の SELECT ステートメントからエラー メッセージが返されます。 その後、このテーブルに対して行われる参照は失敗します。 SET SHOWPLAN_TEXT が OFF の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]せず、実行プラン情報を含むレポートを生成するステートメントを実行します。  
  
 SET SHOWPLAN_TEXT をなどの Microsoft Win32 コマンド プロンプト アプリケーションで読みやすい出力を返すものでは、 **osql**ユーティリティです。 SET SHOWPLAN_ALL を使用するとさらに詳細な出力が返され、その出力を取り扱うように設計されたプログラムで使用できます。  
  
 SET SHOWPLAN_TEXT と SET SHOWPLAN_ALL は、ストアド プロシージャ内に指定できません。 またバッチ内で同時に他のステートメントを実行することもできません。  
  
 SET SHOWPLAN_TEXT がで実行される手順を表す階層ツリーを形成する行のセットとして情報を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ プロセッサの各ステートメントが実行されます。 出力結果には、ステートメントごとに、ステートメントのテキストを示す 1 行と、実行ステップの詳細を示す複数行が含まれます。 次の表に、出力結果に含まれる列を示します。  
  
|列名|Description|  
|-----------------|-----------------|  
|**StmtText**|この列は、種類 PLAN_ROW の場合は行のテキストを含む、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 PLAN_ROW 型の行の場合、この列には操作の説明が含まれます。 またこの列には物理操作と、必要に応じて論理操作が含まれます。 場合によっては、この列の後に説明が含まれます。説明が後に続くかどうかは、物理操作によって決まります。 物理演算子の詳細については、次を参照してください。、**引数**内の列[SET SHOWPLAN_ALL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-showplan-all-transact-sql.md).|  
  
 プラン表示出力でわかるように、物理および論理演算子の詳細については、次を参照してください[プラン表示の論理および物理演算子リファレンス。](../../relational-databases/showplan-logical-and-physical-operators-reference.md)  
  
## <a name="permissions"></a>Permissions  
 SET SHOWPLAN_TEXT を使用するには、SET SHOWPLAN_TEXT の実行ステートメントを実行するための適切な権限が与えられている必要があります。また、参照されるオブジェクトを含むすべてのデータベースに対して、SHOWPLAN 権限が必要です。  
  
 SELECT、INSERT、UPDATE、DELETE、EXEC の*stored_procedure*と EXEC *user_defined_function*ステートメントをユーザーはプラン表示を作成します。  
  
-   実行する適切なアクセス許可、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
-   SHOWPLAN 権限。これは、Transact-SQL ステートメントで参照されるオブジェクト (テーブルやビューなど) を含むすべてのデータベースに対して必要です。  
  
 DDL、USE など、他のすべてのステートメントの*database_name*、セット、DECLARE、動的 SQL、および実行する適切な権限のみで、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが必要です。  
  
## <a name="examples"></a>使用例  
 この例は、によってインデックスを使用する方法を示します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ようにステートメントを処理します。  
  
 インデックスを使用するクエリは次のとおりです。  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 Here is the result set:  
  
```  
StmtText                                             
---------------------------------------------------  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;   
  
StmtText                                                                                                                                                                                        
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Seek(OBJECT:([AdventureWorks2012].[Production].[Product].[PK_Product_ProductID]), SEEK:([AdventureWorks2012].[Production].[Product].[ProductID]=CONVERT_IMPLICIT(int,[@1],0)) ORDERED FORWARD)   
```  
  
 インデックスを使用しないクエリは次のとおりです。  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 Here is the result set:  
  
```  
StmtText                                                                  
------------------------------------------------------------------------  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;   
  
StmtText                                                                                                                                                                                                  
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Scan(OBJECT:([AdventureWorks2012].[Production].[ProductCostHistory].[PK_ProductCostHistory_ProductCostID]), WHERE:([AdventureWorks2012].[Production].[ProductCostHistory].[StandardCost]<[@1]))  
```  
  
## <a name="see-also"></a>参照  
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-showplan-all-transact-sql.md)  
  
  

