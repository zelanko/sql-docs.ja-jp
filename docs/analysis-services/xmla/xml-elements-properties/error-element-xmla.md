---
title: "Error 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Error Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 214dc93af2f02f4bd47ac9d0199b0254fe2ab024
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="error-element-xmla"></a>Error 要素 (XMLA)
  インスタンスによって返されるエラーについての情報を含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
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
|親要素|[メッセージ](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|子要素|次の表を参照してください。|  
  
|Ancestor|子要素|  
|--------------|--------------------|  
|[メッセージ](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|なし|  
|[セル](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md)、[行](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[説明](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md)、 [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md)、 [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md)、[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|ErrorCode|必要な**UnsignedInt**属性 (される場合にのみ**メッセージ**親要素です)。エラーのリターン コード (数値) を含みます。|  
|Severity|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーの重大度レベルを格納します。|  
|Description|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーについての説明テキストを含みます。|  
|ソース|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーを生成したコンポーネントの名前を含みます。|  
|HelpFile|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーについて説明しているヘルプ ファイルまたはトピックのパス、あるいは URL を含みます。|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [Warning 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

