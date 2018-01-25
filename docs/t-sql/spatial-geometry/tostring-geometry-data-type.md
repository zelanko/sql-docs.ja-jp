---
title: "ToString (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ToString (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 614ecad2f669fed40ac5fd7ca30b994bedb0ac6e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="tostring-geometry-data-type"></a>ToString (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

インスタンスに格納されている Z (標高) 値および M (メジャー) 値で補完された geometry インスタンスについて、Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] return type: **nvarchar(max)**  
  
 CLR の戻り値の型: **SqlString**  
  
## <a name="remarks"></a>解説  
 このメソッドは、NULL インスタンスで呼び出されたときに、文字列 "Null" を返します。  
  
 Null 以外のインスタンスでこのメソッドを使用するには`AsTextZM().`  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString`使用して、インスタンス`ToString()`をインスタンスのテキストの説明を取得します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STAsText &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

