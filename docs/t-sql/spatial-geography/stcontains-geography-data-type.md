---
title: "STContains (geography データ型) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STContains method (geography)
ms.assetid: b10e8f0a-2926-449a-82ea-be42543420ca
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a787a75bbf4e9ab54ebc6aab90b64cd74fb50d03
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stcontains--geography-data-type"></a>STContains (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  呼び出し元の **geography** インスタンスに、メソッドに渡される **geography** インスタンスが空間的に含まれるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STContains ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 `STContains()` を呼び出したインスタンスと比較される、別の **geography** インスタンスです。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **bit**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 呼び出し元の **geography** インスタンスに、メソッドに渡される **geography** インスタンスが空間的に含まれる場合は 1 を返します。それ以外の場合は 0 を返します。 2 つの **geography** インスタンスの SRID が同じでない場合は、**null** を返します。  
  
## <a name="examples"></a>使用例  
 `STContains()` を使用して、2 つの `geography` インスタンスの一方のインスタンスがもう一方のインスタンスを含むかどうかをテストする例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SET @h = geography::Parse('POINT(-121.703796 46.893985)');  
```  
  
 `SELECT @g.STContains(@h);`  
  
  
