---
title: ProtocolCapabilities 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85ddeb22fac03e5ae7f66521ac3ca8a46e210fe7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574784"
---
# <a name="protocolcapabilities-element-xmla"></a>ProtocolCapabilities 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services のインスタンスとクライアント アプリケーション間のプロトコル機能を識別するのに、SOAP 要求メッセージの SOAP ヘッダーを使用します。  
  
 **名前空間** `http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[機能](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **ProtocolCapabilities**要素により、クライアント アプリケーションでバイナリ XML や圧縮サポートなどのプロトコル機能をネゴシエートする、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]いつでもインスタンス。 プロトコルのネゴシエーションは以下の手順で行われます。  
  
1.  クライアント アプリケーションは、SOAP ヘッダー内に **ProtocolCapabilities** 要素を含む SOAP 要求を送信することにより、自らのプロトコル機能を示します。  
  
2.  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は SOAP 要求を受信して処理します。  
  
3.  場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスに要求されたものと同じプロトコル機能は、インスタンスが同じを含む SOAP 応答を送信**ProtocolCapabilities**要素が SOAP 要求で送信し、プロトコル、されました正常にネゴシエートします。 そうでない場合、プロトコル機能は正常にネゴシエートされず、インスタンスは SOAP エラーを返します。  
  
 プロトコル機能をどのくらいの時間のクライアント アプリケーションを正常にネゴシエートされた後、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスを使用する特定のプロトコルは、セッションが明示的か暗黙かどうかによって異なります。  
  
-   使用して作成されるものは、明示的なセッション、 [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)ヘッダー要素。 明示的セッションの場合、ネゴシエートされたプロトコルは、クライアント アプリケーションが新しい **ProtocolCapabilities** 要素を送るまで、またはセッションが終了するまで使用されます。  
  
-   暗黙のセッションとは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによって作成されるセッションで、SOAP 要求の送信時にクライアント アプリケーションによって明示的に指定されるものではありません。 暗黙のセッションの場合、ネゴシエートされたプロトコルは、SOAP 要求が完了するまでの期間だけ使用されます。  
  
 プロトコル機能を明示的にネゴシエートする必要はありません。 つまり、クライアント アプリケーションで **ProtocolCapabilities** 要素を SOAP 要求に含める必要はありません。 SOAP 要求が含まれていない場合、 **ProtocolCapabilities**要素、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスは SOAP 要求と同じ形式を使用して応答を行います。  
  
## <a name="see-also"></a>参照
 [接続およびセッション管理&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダー &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
