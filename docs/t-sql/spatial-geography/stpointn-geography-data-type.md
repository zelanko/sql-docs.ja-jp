---
title: "STPointN (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- STPointN_TSQL
- STPointN (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STPointN method
ms.assetid: 47670feb-b9e0-4b4b-af83-b9bba7da66ac
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0169852c4b7512ec3001875cba423bc93e53125e
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="stpointn-geography-data-type"></a>STPointN (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  内の指定された地点を返します、 **geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **Int** 1 ~ 内の地点の数の式、 **geography**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
 Open Geospatial Consortium (OGC) の型:**ポイント**  
  
## <a name="remarks"></a>解説  
 場合、 **geography**インスタンスは、ユーザーが作成した、STPointN() が指定された地点を返します*式*によってを最初に入力した順序で地点を並べ替えます。  
  
 場合、 **geography**インスタンスが、システムによって構築された、STPointN() が指定された地点を返します*式*同じ順序ですべての地点を並べ替えるによって出力される順序によって最初**。geography** (該当する場合)、インスタンス内のリングし、リング内の地点のインスタンス。 この順序は決定的です。  
  
 このメソッドは 1 より小さい値を含む、スロー、 **ArgumentOutOfRangeException**です。  
  
 インスタンス内の地点の数より大きい値を指定してこのメソッドを呼び出すと、メソッドは NULL を返します。  
  
## <a name="examples"></a>使用例  
 `LineString` インスタンスを作成し、`STPointN()` を使用して、このインスタンスの記述に含まれる 2 番目の地点を取得する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
