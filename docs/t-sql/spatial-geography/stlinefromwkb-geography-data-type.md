---
title: "STLineFromWKB (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STLineFromWKB (geography Data Type)
- STLineFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLineFromWKB method
ms.assetid: 8ac2b772-6673-4ba1-a7ab-3b4b5841560b
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2aae934d52c2432f8815c278950138fc644dfd5d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stlinefromwkb-geography-data-type"></a>STLineFromWKB (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **LineString geography** Open Geospatial Consortium (OGC) Well-Known Binary (WKB) 表現からのインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
STLineFromWKB ( 'WKB_linestring' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_linestring*  
 WKB 表現です、 **LineString geography**インスタンスを取得します。 *WKB_linestring*は、 **varbinary (max)**式。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **LineString geography**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
 OGC の型: **LineString**  
  
## <a name="remarks"></a>解説  
 このメソッドは、 **FormatException**入力が適切な形式でない場合。  
  
## <a name="examples"></a>使用例  
 次の例で`STLineFromWKB()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;  
SET @g = geography::STLineFromWKB(0x010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

