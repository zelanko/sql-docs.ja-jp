---
title: EmptyResult データ型 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EmptyResult Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EmptyResult
- olapxmla_EmptyResult
- urn:schemas-microsoft-com:xml-analysis#EmptyResult
helpviewer_keywords:
- EmptyResult data type
ms.assetid: 63818123-acbb-4220-9d60-1aa20a7326a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc22612f18faa91e6cd668c022f036aadb9ef176
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088547"
---
# <a name="emptyresult-data-type-xmla"></a>EmptyResult データ型 (XMLA)
  表す派生データ型を定義、[ルート](../xml-elements-properties/root-element-xmla.md)からデータを返さない要素、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッドの呼び出し。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析: 空  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[結果セット](resultset-data-type-xmla.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|[root](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 XML for Analysis (XMLA) コマンドの中には、結果を返さないものや、エラーのために結果を返すことができないものがあります。 結果を返さない XMLA コマンドは `EmptyResult` データ型 (`root` 要素上の名前空間) を返します。  
  
## <a name="example"></a>例  
 次の例は、結果が空の場合に返される `root` 要素を表しています。  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
