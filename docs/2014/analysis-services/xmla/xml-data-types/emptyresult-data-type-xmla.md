---
title: EmptyResult データ型 (XMLA) |Microsoft ドキュメント
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
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bba727b2d7d612fa59c99665bd16d936da137fb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177389"
---
# <a name="emptyresult-data-type-xmla"></a>EmptyResult データ型 (XMLA)
  表す派生データ型を定義、[ルート](../xml-elements-properties/root-element-xmla.md)要素からデータを返さない、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: 空  
  
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
  
  