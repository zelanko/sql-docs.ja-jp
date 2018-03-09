---
title: "ポイント | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: spatial
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3fd20af212e94f33bf72ca35f6cf674bb46e50d0
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="point"></a>ポイント
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空間データの **Point** は、1 つの場所を表す 0 次元のオブジェクトです。これには、Z (昇格) 値と M (メジャー) 値が含まれる場合もあります。  
  
## <a name="geography-data-type"></a>geography データ型  
 geography データ型の Point 型は、 *Lat* が緯度、 *Long* が経度を表している 1 つの場所を表します。 緯度と経度の値は度数で測定されます。 緯度の値は、常に [-90, 90] の範囲内になります。この範囲外の値が入力されると、例外がスローされます。 経度の値は、常に [-180, 180] の範囲内になります。この範囲外の入力値は、この範囲に収まるように調整されます。 たとえば、経度の値として 190 を入力した場合は、値 -170 に調整されます。 *SRID* は、返される **geography** インスタンスの空間参照 ID を表します。  
  
## <a name="geometry-data-type"></a>geometry データ型  
 geometry データ型の Point 型は、 *X* が生成される Point の X 座標、 *Y* が生成される Point の Y 座標を表している 1 つの場所を表します。 *SRID* は、返される **geometry** インスタンスの空間参照 ID を表します。  
  
## <a name="examples"></a>使用例  
 次の例では、点 (3, 4) を表す `geometry Point`インスタンスを作成します。このインスタンスの SRID は 0 です。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 次の例では、SRID が 0 (既定)、Z (昇格) 値が 7、M (メジャー) 値が 2.5 の、点 (3, 4) を表す `geometry``Point` インスタンスを作成します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 最後の例では、 `geometry``Point` インスタンスの X、Y、Z、および M の値を返します。  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 Z と M の値は、次の例のように明示的に NULL として指定することもできます。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a>参照  
 [MultiPoint](../../relational-databases/spatial/multipoint.md)   
 [STX &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
