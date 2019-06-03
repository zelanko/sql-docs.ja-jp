---
title: ReorientObject (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ReorientObject
- ReorientObject_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ReorientObject method (geography)
ms.assetid: e2a1a4f1-211b-4e82-abed-03fc7140a83c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: e2945b08eaf0a22c6c83bd412e97c729bedfdfea
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65936354"
---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

内部領域と外部領域が入れ替えられた **geography** インスタンスを返します。  
  
この **geography** データ型メソッドは、半球より大きい **FullGlobe** インスタンスまたは空間インスタンスをサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.ReorientObject (geography)  
```  
  
## <a name="arguments"></a>引数  
_geography_  
`ReorientObject()` を呼び出したときの別の **geography** インスタンスです。  
  
## <a name="return-value"></a>戻り値  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
CLR の戻り値の型:**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
このメソッドでは、**GeometryCollection** 内のすべての **Polygons** のリングの方向が変更されますが、指定されたコレクション内の **Points** または **Linestrings** はいずれも削除または変更されません。  
  
このメソッドに **GeometryCollection** を渡すと、そのコレクション内の各インスタンスの方向が変更されますが、コレクション全体の方向は変更されません。  
  
## <a name="examples"></a>使用例  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>参照  
[Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
