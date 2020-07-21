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
ms.openlocfilehash: 2cb6064347176b34e4141e8c7c5c3bf466669145
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85705671"
---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (geography データ型)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

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
  
CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
このメソッドでは、**GeometryCollection** 内のすべての **Polygons** のリングの方向が変更されますが、指定されたコレクション内の **Points** または **Linestrings** はいずれも削除または変更されません。  
  
このメソッドに **GeometryCollection** を渡すと、そのコレクション内の各インスタンスの方向が変更されますが、コレクション全体の方向は変更されません。  
  
## <a name="examples"></a>例  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>参照  
[Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
