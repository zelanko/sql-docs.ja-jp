---
title: "ToString (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ToString (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26affe3f63d15d92ed672ef2f9dd083ca658cb44
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="tostring-geography-data-type"></a>ToString (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します、 **geography**いる Z (標高) 値および M (メジャー) 値で補完されたインスタンスがインスタンスで実行します。  
  
 この geography データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **nvarchar (max)**  
  
 CLR の戻り値の型: **SqlString**  
  
## <a name="remarks"></a>解説  
 このメソッドは、NULL インスタンスで呼び出されたときに文字列 "Null" を返します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、サーバーで結果セットが拡張されて**FullGlobe**インスタンス。 このメソッドは、同じ値を返します`AsTextZM()`です。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString`使用して、インスタンス`ToString()`をインスタンスのテキスト説明を返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM &#40;geography データ型&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
