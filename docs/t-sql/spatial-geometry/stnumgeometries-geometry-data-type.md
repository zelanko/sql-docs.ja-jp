---
title: STNumGeometries (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
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
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d237641d719df7c9549896ea12218e2de49d1fd8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** インスタンスを構成するジオメトリの数を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、**geometry** インスタンスが **MultiPoint**、**MultiLineString**、**MultiPolygon**、**GeometryCollection** インスタンスではない場合に 1 を返し、**geometry** インスタンスが空の場合に 0 を返します。  
  
> [!NOTE]  
>  **GeometryCollection** に入れ子になった空の要素がある場合は、`STNumGeometries()` は 0 を返しません。 **GeometryCollection** インスタンス内の要素は空ですが、インスタンス自体は空のセットではありません。  
  
  

