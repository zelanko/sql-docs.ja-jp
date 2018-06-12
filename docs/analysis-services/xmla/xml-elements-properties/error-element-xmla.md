---
title: Error 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f223bff2dced01c2b3f954ca14242b1a35c93813
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576554"
---
# <a name="error-element-xmla"></a>Error 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services のインスタンスによって返されるエラーについての情報が含まれています。  
  
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
|説明|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーについての説明テキストを含みます。|  
|Source|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーを生成したコンポーネントの名前を含みます。|  
|HelpFile|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーについて説明しているヘルプ ファイルまたはトピックのパス、あるいは URL を含みます。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照
 [Warning 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
