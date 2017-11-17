---
title: "STMPointFromText (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STMPointFromText (geometry Data Type)
- STMPointFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPointFromText (geometry Data Type)
ms.assetid: 37059074-5ee8-4f55-9414-1e958fd3adaf
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9df0e2b397a82a85c1ecdea87f6159c9b5c99905
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stmpointfromtext-geometry-data-type"></a>STMPointFromText (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **geometry**いる Z (標高) 値および M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現からのインスタンスがインスタンスで実行します。
  
## <a name="syntax"></a>構文  
  
```  
  
STMPointFromText ( 'multipoint_tagged_text', SRID )  
```  
  
## <a name="arguments"></a>引数  
 *multipoint_tagged_text*  
 WKT 表現です、 **geometryMultiPoint**インスタンスを取得します。 *multipoint_tagged_text*は、 **nvarchar (max)**式。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geometryMultiPoint**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
 OGC の型: **MultiPoint**  
  
## <a name="remarks"></a>解説  
 このメソッドはスロー、 **FormatException**入力が適切な形式でない場合。  
  
## <a name="examples"></a>使用例  
 次の例で`STMPointFromText()`を作成する、`geometry`インスタンス。  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STMPointFromText('MULTIPOINT ((100 100), (200 200))', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的なジオメトリ メソッド](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  


