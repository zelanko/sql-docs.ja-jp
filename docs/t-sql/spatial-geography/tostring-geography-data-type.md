---
title: ToString (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ToString (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fcd5618e6bfa434a3f31ab4817f53114e122846d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85701506"
---
# <a name="tostring-geography-data-type"></a>ToString (geography データ型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  インスタンスに格納されている Z (標高) 値および M (メジャー) 値で補完された **geography** インスタンスについて、Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します。  
  
 この geography データ型メソッドは、半球より大きい **FullGlobe** インスタンスまたは空間インスタンスをサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **nvarchar(max)**  
  
 CLR の戻り値の型: **SqlString**  
  
## <a name="remarks"></a>解説  
 このメソッドは、NULL インスタンスで呼び出されたときに文字列 "Null" を返します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、サーバー上で使用可能な結果セットが **FullGlobe** インスタンスに拡張されています。 このメソッドは、`AsTextZM()` と同じ値を返します。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>例  
 `LineString` インスタンスを作成し、`ToString()` を使用してインスタンスの記述を返す例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM &#40;geography データ型&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
