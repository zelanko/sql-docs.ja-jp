---
title: "ISJSON (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0ecbcc4ced2b9503ec9161f7aa93a1a5266960ef
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="isjson-transact-sql"></a>ISJSON (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  有効な JSON を含む文字列であるかどうかをテストします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 テストする文字列です。  
  
## <a name="return-value"></a>戻り値  
 有効な JSON です。 が、文字列に含まれている場合は 1 を返します。それ以外の場合は 0 を返します。 場合は null を返します*式*が null です。  
  
 エラーは返されません。  
  
## <a name="remarks"></a>解説  
 **ISJSON**同じレベルのキーの一意性を確認しません。  
  
## <a name="examples"></a>使用例  
  
### <a name="example-1"></a>例 1  
次の例、ステートメント ブロックが実行条件付きで場合、パラメーター値`@param`有効な JSON が含まれています。  
  
```sql  
DECLARE @param <data type>
SET @param = <value>

IF (ISJSON(@param) > 0)  
BEGIN  
     -- Do something with the valid JSON value of @param.  
END
 
```  
  
### <a name="example-2"></a>例 2  
次の例は、列 `json_col` に有効な JSON が含まれている行を返します。  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  
  
## <a name="see-also"></a>参照  
 [JSON データ &#40;です。SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
