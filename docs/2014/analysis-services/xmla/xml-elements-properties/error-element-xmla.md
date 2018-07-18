---
title: Error 要素 (XMLA) |Microsoft Docs
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
- Error Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 55b63c016f9f2c61cc83563e697a49a0c4970cae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273738"
---
# <a name="error-element-xmla"></a>Error 要素 (XMLA)
  インスタンスによって返されるエラーについての情報を含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
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
|親要素|[メッセージ](message-element-xmla.md)|  
  
## <a name="child-elements"></a>子要素  
  
|Ancestor|子要素|  
|--------------|--------------------|  
|[メッセージ](message-element-xmla.md)|なし|  
|[セル](cell-element-mddataset-xmla.md)、[行](description-element-xmla.md)、 [ErrorCode](errorcode-element-xmla.md)、 [HelpFile](file-element-xmla.md)、[ソース](source-element-error-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|ErrorCode|必要な`UnsignedInt`属性 (場合にのみ`Message`は親要素です)。エラーのリターン コード (数値) を含みます。|  
|Severity|省略可能な`String`属性 (場合にのみ`Message`は親要素です)。エラーの重大度レベルを格納します。|  
|説明|省略可能な`String`属性 (場合にのみ`Message`は親要素です)。エラーについての説明テキストを含みます。|  
|Source|省略可能な`String`属性 (場合にのみ`Message`は親要素です)。エラーを生成したコンポーネントの名前を含みます。|  
|HelpFile|省略可能な`String`属性 (場合にのみ`Message`は親要素です)。エラーについて説明しているヘルプ ファイルまたはトピックのパス、あるいは URL を含みます。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [Warning 要素&#40;XMLA&#41;](warning-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
