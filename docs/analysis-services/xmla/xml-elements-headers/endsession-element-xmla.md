---
title: "EndSession 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EndSession Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EndSession
- urn:schemas-microsoft-com:xml-analysis#EndSession
- microsoft.xml.analysis.endsession
helpviewer_keywords: EndSession element
ms.assetid: e64f1da4-5c83-40a2-b15e-837f5451bafa
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9cc62b7d87aeaade6984b44c7724de120b17dcaf
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="endsession-element-xmla"></a>EndSession 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]インスタンス上の既存のセッションを終了する SOAP 要求メッセージの SOAP ヘッダーを使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
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
|子要素|なし|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|SessionId|必要な**文字列**終了するセッションを識別する属性。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はグローバル一意識別子 (GUID) を使用してセッションを識別します。|  
  
## <a name="remarks"></a>解説  
 **EndSession**ヘッダー要素明示的に開始された既存のセッションに送信される SOAP 要求の一部である、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 場合、 **EndSession**ヘッダー要素が送信されますが、有効では不要になったセッション識別子を含む、セッションが見つからないことを示す SOAP エラーが返されます。  
  
## <a name="see-also"></a>参照  
 [BeginSession 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [Session 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [管理接続およびセッション (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダーと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
