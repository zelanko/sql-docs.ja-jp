---
title: Name プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
author: rothja
ms.author: jroth
ms.openlocfilehash: 370dc7900e5fe876ea1b1064b2621371c730f323
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765103"
---
# <a name="name-property-ado-md"></a>Name プロパティ (ADO MD)
オブジェクトの名前を示します。  
  
## <a name="return-values"></a>戻り値  
 は**文字列**を返し、読み取り専用です。  
  
## <a name="remarks"></a>Remarks  
 オブジェクトの**name**プロパティは、序数参照によって取得できます。その後、オブジェクトを名前で直接参照できます。 たとえば、に `cdf.CubeDefs(0).Name` よって "Bobs ビデオストア" が生成された場合、この[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)をと呼び出すことができ `cdf.CubeDefs("Bobs Video Store")` ます。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axis オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Catalog オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Dimension オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Level オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>参照  
 [カタログの例 (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Caption プロパティ (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Description プロパティ (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName プロパティ (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
