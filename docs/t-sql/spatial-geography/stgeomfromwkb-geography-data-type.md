---
title: "STGeomFromWKB (geography データ型) |Microsoft ドキュメント"
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
f1_keywords:
- STGeomFromWKB_TSQL
- STGeomFromWKB (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STGeomFromWKB method
ms.assetid: 79d39d88-5440-49a7-9247-190eafce3f4f
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 984271f301a641c72eb8a0eef5f5153ba7bfd5f1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="stgeomfromwkb-geography-data-type"></a>STGeomFromWKB (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **geography** Open Geospatial Consortium (OGC) Well-Known Binary (WKB) 表現からのインスタンス。
  
これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。
  
## <a name="syntax"></a>構文  
  
```  
  
STGeomFromWKB ( 'WKB_geography' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_geography*  
 WKB 表現です、 **geography**インスタンスを返します。 *WKB_geography*は、 **varbinary (max)**式。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geography**インスタンスを返します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geography**によって返されるインスタンス`STGeomFromText()`が、対応する WKB 入力に設定します。  
  
 このメソッドは、 **FormatException**入力が適切な形式でない場合。  
  
 このメソッドはスロー **ArgumentException**場合は、入力に対蹠が含まれています。  
  
## <a name="examples"></a>使用例  
 次の例で`STGeomFromWKB()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromWKB(0x010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
