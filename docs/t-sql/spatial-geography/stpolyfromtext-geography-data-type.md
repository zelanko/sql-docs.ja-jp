---
title: STPolyFromText (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPolyFromText_TSQL
- STPolyFromText (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromText method
ms.assetid: d7e6a2bb-d301-49fb-9202-c70a9d169b4d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 02232606ccfba5c03793dd6a3bff515efd0c8e6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47744510"
---
# <a name="stpolyfromtext-geography-data-type"></a>STPolyFromText (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

インスタンスに格納されている Z (標高) 値および M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現を基に **geography** インスタンスを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
STPolyFromText ( 'polygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *polygon_tagged_text*  
 返される **geographyPolygon** インスタンスの WKT 表現です。 *polygon_tagged_text* は **nvarchar(max)** 式です。  
  
 *SRID*  
 返される **geographyPolygon** インスタンスの SRID (spatial reference ID) を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR 戻り値の型: **SqlGeography**  
  
 OGC の型: **Polygon**  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、入力が整形式でない場合に、**FormatException** がスローされます。  
  
## <a name="examples"></a>使用例  
 `STPolyFromText()` を使用して `geography` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STPolyFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
