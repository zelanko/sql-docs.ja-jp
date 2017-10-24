---
title: "STNumGeometries (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c8ca87eeff2f807b55754d9d9adf19ebf03a4fd8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

構成するジオメトリの数を返します、 **geometry**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>解説  
 場合 1 を返します、 **geometry**インスタンスではありません、 **MultiPoint**、 **MultiLineString**、 **MultiPolygon**、または**GeometryCollection**インスタンス、および 0 の場合、 **geometry**インスタンスが空です。  
  
> [!NOTE]  
>  場合、 **GeometryCollection**に空の要素を入れ子になった`STNumGeometries()`は 0 を返しません。 ただし内の要素、 **GeometryCollection**インスタンスが空では、インスタンス自体は空のセットではありません。  
  
  


