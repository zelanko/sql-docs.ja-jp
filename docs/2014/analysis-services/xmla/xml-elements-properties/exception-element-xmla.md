---
title: Exception 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Exception Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e447bda3d52ac63125f3a96769fcee2c0158494c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178542"
---
# <a name="exception-element-xmla"></a>Exception 要素 (XMLA)
  例外が返されたことを示します、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッドの呼び出し。  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/exception  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
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
|親要素|[root](root-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Discover` メソッド呼び出しの実行時、または `Execute` メソッド呼び出し内の単一の XMLA コマンドの実行時にエラーが発生して、メソッドまたはコマンドが完了しない場合には、そのメソッドまたはコマンドの `root` 要素に `Exception` 要素および `Messages` 要素が格納されます。 `Exception` 要素は、エラーが発生してメソッドまたはコマンドが正常に実行されなかったことを示し、`Messages` 要素は、そのエラーに関連したエラー メッセージまたは警告メッセージの一覧を含みます。  
  
## <a name="see-also"></a>参照  
 [要素をメッセージ&#40;XMLA&#41;](messages-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
