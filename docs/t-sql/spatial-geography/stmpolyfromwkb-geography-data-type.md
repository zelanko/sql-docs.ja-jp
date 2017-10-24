---
title: "STMPolyFromWKB (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STMPolyFromWKB (geography Data Type)
- STMPolyFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPolyFromWKB method
ms.assetid: c4d0e649-0abb-4343-a3f0-3a702c8bbbdb
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7c5bfa3ca900ffde7a68d378ff21e8314ff69c3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stmpolyfromwkb-geography-data-type"></a>STMPolyFromWKB (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **geographyMultiPolygon** Open Geospatial Consortium (OGC) Well-Known Binary (WKB) 表現からのインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
STMPolyFromWKB ( 'WKB_multipolygon' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_multipolygon*  
 WKB 表現です、 **geographyMultiPolygon**インスタンスを取得します。 *WKB_multipolygon*は、 **varbinary (max)**式。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geographyMultiPolygon**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
 OGC の型: **MultiPolygon**  
  
## <a name="examples"></a>使用例  
 次の例で`STMPolyFromWKB()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;  
SET @g = geography::STMPolyFromWKB(0x01060000000200000001030000000100000004000000F4FDD478E9965EC0DD24068195D3474083C0CAA145965EC0508D976E12D34740F4FDD478E9965EC04E62105839D44740F4FDD478E9965EC0DD24068195D3474001030000000100000004000000E7FBA9F1D2955EC08716D9CEF7D34740E7FBA9F1D2955EC0F853E3A59BD447405839B4C876965EC0F853E3A59BD44740E7FBA9F1D2955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

