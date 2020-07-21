---
title: DEGREES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DEGREES
- DEGREES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DEGREES function
- number of degrees
ms.assetid: 5208de3c-90a3-4f59-a7e3-10b01bf285bb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7fb2e184245b526c3cacc18fa8b7003625e27fcf
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86005925"
---
# <a name="degrees-transact-sql"></a>DEGREES (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

この関数は、ラジアン単位で指定された角度に対して、対応する角度を度の単位で返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```syntaxsql
DEGREES ( numeric_expression )  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
[bit](../../t-sql/language-elements/expressions-transact-sql.md) データ型を除く、真数または概数データ型カテゴリの**式**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
データ型が *numeric_expression* のデータ型に一致する値を返します。  
  
## <a name="examples"></a>例  
この例では、PI/2 ラジアンの角度を度の単位で返します。  
  
```  
SELECT 'The number of degrees in PI/2 radians is: ' +   
CONVERT(VARCHAR, DEGREES((PI()/2)));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The number of degrees in PI/2 radians is 90         
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [数学関数 &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
