---
title: "結果の要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: results Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords: results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3b68533f174d5502c77d94be70aab4f0ff676071
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="results-element-xmla"></a>results 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]コレクションを格納[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)要素によって返される、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドを使用して、[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンド。  
  
 **Namespace**`http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[戻り値](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|子要素|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 場合、**バッチ**によってコマンドを実行、 **Execute** 、メソッド、**返す**要素には、1 つが含まれています**結果**要素の代わりに、。1 つ**ルート**要素。 内容、**結果**要素は、実行に使用される設定によって異なります、**バッチ**コマンド。  
  
 非トランザクション**バッチ**コマンド、**結果**要素を 1 つ**ルート**で実行される各コマンドの要素、**バッチ**コマンド、コマンドは成功と失敗が完了するかどうか。 トランザクション**バッチ**コマンドを**結果**要素は 1 つだけ**ルート**要素は、内で失敗したコマンドのエラー情報が含まれています、**バッチ**コマンド。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
