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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c248139abfd136d5c79658592e0e49d5e10444aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949395"
---
# <a name="name-property-ado-md"></a>Name プロパティ (ADO MD)
オブジェクトの名前を示します。  
  
## <a name="return-values"></a>戻り値  
 は**文字列**を返し、読み取り専用です。  
  
## <a name="remarks"></a>Remarks  
 オブジェクトの**name**プロパティは、序数参照によって取得できます。その後、オブジェクトを名前で直接参照できます。 たとえば、によっ`cdf.CubeDefs(0).Name`て "Bobs ビデオストア" が生成された場合、この`cdf.CubeDefs("Bobs Video Store")` [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)をと呼び出すことができます。  
  
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
