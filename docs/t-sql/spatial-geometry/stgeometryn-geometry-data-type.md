---
title: STGeometryN (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STGeometryN_TSQL
- STGeometryN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN (geometry Data Type)
ms.assetid: 348c7047-3442-4590-8879-fe841e79058c
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 51ec03e3e12dc48920aa1748c9ccd343ee55b8bf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36253254"
---
# <a name="stgeometryn-geometry-data-type"></a>STGeometryN (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry コレクション**で指定されたジオメトリを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 1 から **geometrycollection** に含まれる **geometry** インスタンスの数までの数値を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 パラメーターが `STNumGeometries()` の結果よりも大きい場合、このメソッドは **null** を返します。また、*expression* パラメーターが 1 より小さい場合は、**ArgumentOutOfRangeException** をスローします。  
  
## <a name="examples"></a>使用例  
 `MultiPoint``geometry collection` を作成し、`STGeometryN()` を使用してコレクションの 2 番目の `geometry` インスタンスを探す例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

