---
title: SRID (Spatial Reference Identifier) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 57420f270daa88e61add4810a7792ed6fdea8278
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="spatial-reference-identifiers-srids"></a>SRID (Spatial Reference Identifier)
  各空間インスタンスには SRID (spatial reference identifier) があります。 SRID は、平面地球マッピングまたは球体地球マッピングに使用される特定の楕円体に基づく空間参照系に対応します。  
  
> [!IMPORTANT]  
>  新しい SRID を含む、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入された空間機能の詳細な説明とサンプルについては、ホワイト ペーパー「 [New Spatial Features in SQL Server 2012 (SQL Server 2012 の新しい空間機能)](http://go.microsoft.com/fwlink/?LinkId=226407)」をダウンロードして参照してください。  
  
 空間列には異なる SRID を持つオブジェクトを格納できますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の空間データ メソッドを使用してデータの操作を実行する際に使用できるのは、同じ SRID を持つ空間インスタンスだけです。 2 つの空間データ インスタンスから引き出される空間メソッドの結果は、それらのインスタンスが同じ SRID を持つ (同じ測定単位、データ、および投影を使用してインスタンスの座標が決定されている) 場合にのみ有効になります。 SRID の最も一般的な測定単位はメートルまたは平方メートルです。  
  
 2 つの空間インスタンスの SRID が同じでない場合に、それらのインスタンスに対して **geometry** データ型や **geography** データ型のメソッドを使用すると、NULL が返されます。 たとえば、次の述語で NULL 以外の結果が返されるためには、 **および** の 2 つの `geometry1` geometry `geometry2`インスタンスの SRID が同じである必要があります。  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  空間参照識別系は、地図制作、測量、および測地のデータの格納のために開発された一連の標準である [European Petroleum Survey Group (EPSG)](http://go.microsoft.com/fwlink/?LinkId=99349) 標準によって定義されています。 この標準は、Oil and Gas Producers (OGP) Surveying and Positioning Committee が所有しています。  
  
## <a name="see-also"></a>参照  
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  

