---
title: Capability 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Capability Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
caps.latest.revision: 16
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 7fd495ff0abf921b377526f6030d5207d962e1bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075574"
---
# <a name="capability-element-xmla"></a>Capability 要素 (XMLA)
  親のプロトコル機能のサポートを示す[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)ヘッダー要素。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Capability`要素は、バイナリや圧縮など、特定の機能が含まれているか、アプリケーションでサポートされていることを示します、`ProtocolCapabilities`またはのインスタンスによって SOAP 要求の SOAP ヘッダー内のヘッダー要素[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]含まれている、 `ProtocolCapabilities` SOAP 応答の SOAP ヘッダー内のヘッダー要素。 `Capability` 要素の値は、サポートされる機能の名前です。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、以下の表に示す機能がサポートされます。  
  
|機能名|説明|  
|---------------------|-----------------|  
|sx|バイナリ XML サポート|  
|xpress|圧縮サポート|  
  
## <a name="see-also"></a>参照  
 [接続およびセッション管理&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  