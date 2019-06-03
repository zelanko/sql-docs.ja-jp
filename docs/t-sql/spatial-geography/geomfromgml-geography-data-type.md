---
title: GeomFromGML (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 1d5542501325fb84b31c0133aaa04aa0097c077b
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937833"
---
# <a name="geomfromgml-geography-data-type"></a>GeomFromGML (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Geography Markup Language (GML) の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブセットによる表現を指定して **geography** インスタンスを構築します。
  
GML の詳細については、次の Open Geospatial Consortium の仕様を参照してください。[OGC の仕様、Geography Markup Language](https://go.microsoft.com/fwlink/?LinkId=93629)
  
この **geography** データ型メソッドは、半球より大きい **FullGlobe** インスタンスまたは空間インスタンスをサポートします。
  
## <a name="syntax"></a>構文  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>引数  
 *GML_input*  
 GML が返す値を含む XML 入力です。  
  
 *SRID*  
 返される **geography** インスタンスの SRID (spatial reference ID) を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR の戻り値の型:**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、入力が整形式でない場合に、**FormatException** がスローされます。  
  
 このメソッドは、この入力に対蹠点が含まれている場合、**ArgumentException** をスローします。  
  
## <a name="examples"></a>使用例  
 `GeomFromGml()` を使用して `geography` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="https://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
 `GeomFromGml()` を使用して `FullGlobe``geography` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<FullGlobe xmlns="https://schemas.microsoft.com/sqlserver/2011/geography" />';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
