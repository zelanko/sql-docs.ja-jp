---
title: Lat (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Lat
- Lat_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Lat method
ms.assetid: 051d66bc-04de-4c58-861c-760dc5b859b5
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7f07a19d7844d4644d1211cfe4d2c1b71651960
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="lat-geography-data-type"></a>Lat (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスの緯度プロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
.Lat  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の型: **float**  
  
 CLR の型: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 OpenGIS モデルでは、Lat は単一地点のデータで構成される **geography** インスタンスにのみ定義されます。 **geography** インスタンスに複数の地点が含まれる場合、このプロパティは NULL を返します。 このプロパティは正確で、読み取り専用です。  
  
## <a name="examples"></a>使用例  
 この例では、ある地点を作成して、その地点の緯度を返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Lat;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
