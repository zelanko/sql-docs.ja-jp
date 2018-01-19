---
title: "解析 (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32d8925fdf53a1d0bcac33719348138b354376c2
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="parse-geography-data-type"></a>Parse (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **geography** Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現からのインスタンス。 Parse() は等価[STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)spatial reference ID (SRID) 4326 をパラメーターとして想定する点を除いて、します。 入力には、オプションとして Z (標高) 値と M (メジャー) 値が含まれる場合があります。
  
これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。
  
## <a name="syntax"></a>構文  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>引数  
 *geography_tagged_text*  
 WKT 表現です、 **geography**インスタンスを返します。 *geography_tagged_text*は、 **nvarchar**式。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geography**によって返されるインスタンス`Parse()`が、対応する WKT 入力に設定します。  
  
 'Null'、として解釈されます、null 文字列**geography**インスタンス。  
  
 このメソッドはスロー **ArgumentException**場合は、入力に対蹠が含まれています。  
  
## <a name="examples"></a>使用例  
 次の例で`Parse()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText &#40;geography データ型&#41;](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
