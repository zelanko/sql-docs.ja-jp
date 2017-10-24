---
title: "GeomFromGML (geography データ型) |Microsoft ドキュメント"
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
- GeomFromGML_TSQL
- GeomFromGML
dev_langs:
- TSQL
helpviewer_keywords:
- GeomFromGML (geography Data Type)
- GeomFromGML method
ms.assetid: 470d0997-3cb0-4d34-9a45-b332fe432b14
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ec0d21afb92b000f29fb91c4e3b848b4881b99c7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="geomfromgml-geography-data-type"></a>GeomFromGML (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

構築、 **geography** 、表現が指定されたインスタンス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Geography Markup Language (GML) のサブセットです。
  
GML の詳細については、次の Open Geospatial Consortium 仕様を参照してください: [OGC の仕様、Geography Markup Language](http://go.microsoft.com/fwlink/?LinkId=93629)
  
これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。
  
## <a name="syntax"></a>構文  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>引数  
 *GML_input*  
 XML 入力は、GML が値を返します。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geography**インスタンスを返します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドは、 **FormatException**入力が適切な形式でない場合。  
  
 このメソッドはスロー **ArgumentException**入力に対蹠が含まれている場合。  
  
## <a name="examples"></a>使用例  
 次の例で`GeomFromGml()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
 次の例で`GeomFromGml()`を作成する、`FullGlobe``geography`インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<FullGlobe xmlns="http://schemas.microsoft.com/sqlserver/2011/geography" />';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

