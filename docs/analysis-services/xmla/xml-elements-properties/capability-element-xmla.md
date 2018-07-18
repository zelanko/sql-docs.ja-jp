---
title: Capability 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: dca8f668f64ab8ced157cf817be1f9f8f6390133
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062980"
---
# <a name="capability-element-xmla"></a>Capability 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親でプロトコル機能のサポートを示します[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)ヘッダー要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **機能**要素は、バイナリや圧縮などの特定の機能が含まれているか、アプリケーションでサポートされていることを示します、 **ProtocolCapabilities**ヘッダー要素で、SOAP ヘッダーの SOAP 要求または含まれている Analysis Services のインスタンスによって、 **ProtocolCapabilities** SOAP 応答の SOAP ヘッダー内のヘッダー要素。 値、**機能**要素がサポートされる機能の名前。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、以下の表に示す機能がサポートされます。  
  
|機能名|説明|  
|---------------------|-----------------|  
|sx|バイナリ XML サポート|  
|xpress|圧縮サポート|  
  
## <a name="see-also"></a>参照
 [接続およびセッション管理&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
