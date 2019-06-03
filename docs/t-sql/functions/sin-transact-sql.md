---
title: SIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIN_TSQL
- SIN
dev_langs:
- TSQL
helpviewer_keywords:
- SIN function
- sine
ms.assetid: bc1781e9-185f-4981-929b-e77371be6b26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3e128dcd40a3198a7971a6ee9ac69fdac680577
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65947815"
---
# <a name="sin-transact-sql"></a>SIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ラジアンでと概数型の場合、指定された角度の三角関数サインが返されます **float**, 、式です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SIN ( float_expression )  
```  
  

## <a name="arguments"></a>引数  
 *float_expression*  
 **float** 型、または暗黙的に float 型に変換できる[式](../../t-sql/language-elements/expressions-transact-sql.md)を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **float**  
  
## <a name="examples"></a>使用例  
 次の例では、指定された角度の SIN を計算します。  
  
```  
DECLARE @angle float;  
SET @angle = 45.175643;  
SELECT 'The SIN of the angle is: ' + CONVERT(varchar,SIN(@angle));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The SIN of the angle is: 0.929607                         
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、指定された角度の sine を計算します。  
  
```  
SELECT SIN(45.175643);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
---------  
0.929607
```  
  
## <a name="see-also"></a>参照  
 [数学関数 &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

