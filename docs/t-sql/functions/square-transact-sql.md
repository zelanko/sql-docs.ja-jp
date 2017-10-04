---
title: "正方形 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQUARE
- SQUARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: 007b6b12-da86-4229-8f5c-fdd4fa839f5f
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e73ef776e4318b0957838f95bb78601c3de55840
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="square-transact-sql"></a>SQUARE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  指定した浮動小数点値の 2 乗を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SQUARE ( float_expression )  
```  
  
## <a name="arguments"></a>引数  
 *float_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)型の**float**または float 型に暗黙的に変換できる型です。  
  
## <a name="return-types"></a>戻り値の型  
 **float**  
  
## <a name="examples"></a>使用例  
 次の例は、半径の円柱のボリュームを返して`1`インチ、高さは`5`(インチ)。  
  
```  
DECLARE @h float, @r float;  
SET @h = 5;  
SET @r = 1;  
SELECT PI()* SQUARE(@r)* @h AS 'Cyl Vol';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Cyl Vol  
--------------------------  
15.707963267948966  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、内の各値の 2 乗を返します、`volume`内の列、`containers`テーブル。  
  
```  
-- Uses AdventureWorks  
  
CREATE TABLE Containers (  
    ID int NOT NULL,  
    Name varchar(20),  
    Volume float(24));  
  
INSERT INTO Containers VALUES (1, 'Cylinder', '125.22');  
INSERT INTO Containers VALUES (2, 'Cube', '23.98');  
  
SELECT Name, SQUARE(Volume) AS VolSquared   
FROM Containers;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Name           VolSquared`  
  
 `-------------  ----------`  
  
 `Cylinder       15680.05`  
  
 `Cube             575.04`  
  
## <a name="see-also"></a>参照  
 [数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  


