---
title: 結果の要素 (XMLA) |Microsoft ドキュメント
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
- results Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 203ad5a79938c80e2bfccc798ff5f9551ac66d8d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077399"
---
# <a name="results-element-xmla"></a>results 要素 (XMLA)
  コレクションを格納[ルート](root-element-xmla.md)要素によって返される、 [Execute](../xml-elements-methods-execute.md)メソッドを使用して、[バッチ](../xml-elements-commands/batch-element-xmla.md)コマンド。  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
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
|親要素|[return](return-element-xmla.md)|  
|子要素|[root](root-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Batch` コマンドが `Execute` メソッドによって実行される場合、`return` 要素には 1 つの `results` 要素ではなく、1 つの `root` 要素が含まれます。 `results` 要素の内容は、`Batch` コマンド実行時の設定によって異なります。  
  
 非トランザクション型の `Batch` コマンドの場合、`results` 要素には `root` コマンドによって実行された各コマンドごとに、そのコマンドが正常に完了した場合もしなかった場合も 1 つの `Batch` 要素が含まれます。 トランザクション型の `Batch` コマンドの場合、`results` 要素には `root` コマンド内で失敗したコマンドに関するエラー情報を含む `Batch` 要素が 1 つだけ含まれます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  