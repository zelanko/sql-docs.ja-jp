---
title: "Long (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Long_TSQL
- Long
dev_langs:
- TSQL
helpviewer_keywords:
- Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0c69ce921e8aa22d65011a56d47c5cd7b05ad76f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="long-geography-data-type"></a>Long (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  経度プロパティ、 **geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>戻り値  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型: **float**  
  
 CLR 型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 OpenGIS モデルで長いで定義されているのみ**geography**インスタンスは、単一のポイントで構成されます。 場合、このプロパティは NULL を返しますが**geography**インスタンスには、複数の単一のポイントが含まれています。 このプロパティは正確で、読み取り専用です。  
  
## <a name="examples"></a>使用例  
 この例で作成、**ポイント**インスタンスし、その地点の経度を取得します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

