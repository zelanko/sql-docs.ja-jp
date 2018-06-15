---
title: ISJSON (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
caps.latest.revision: 12
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: 0f9bac83281c419209e54553a8c7de968ec35680
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33051069"
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
 有効な JSON です。 が、文字列に含まれている場合は 1 を返します。それ以外の場合は 0 を返します。 *式* が null の場合は null を返します。  
  
 エラーは返されません。  
  
## <a name="remarks"></a>Remarks  
 **ISJSON** は、同じレベルのキーの一意性をチェックしません。  
  
## <a name="examples"></a>使用例  
  
### <a name="example-1"></a>例 1  
次の例では、パラメーター値 `@param` に有効な JSON が含まれている場合は、ステートメント ブロックを条件付きで実行します。  
  
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
 [JSON データ &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
