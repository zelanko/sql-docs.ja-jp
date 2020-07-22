---
title: Lat (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Lat
- Lat_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Lat method
ms.assetid: 051d66bc-04de-4c58-861c-760dc5b859b5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: ede92951517dcbe8c5a58e27bb8db9573fd0354e
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552907"
---
# <a name="lat-geography-data-type"></a>Lat (geography データ型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  **geography** インスタンスの緯度プロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
.Lat  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>戻り値の型
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の型: **float**  
  
 CLR の型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 OpenGIS モデルでは、Lat は単一地点のデータで構成される **geography** インスタンスにのみ定義されます。 **geography** インスタンスに複数の地点が含まれる場合、このプロパティは NULL を返します。 このプロパティは正確で、読み取り専用です。  
  
## <a name="examples"></a>例  
 この例では、ある地点を作成して、その地点の緯度を返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Lat;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
