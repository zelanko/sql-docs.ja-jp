---
title: Database 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Database Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.database
- http://schemas.microsoft.com/analysisservices/2003/engine#Database
- urn:schemas-microsoft-com:xml-analysis#Database
helpviewer_keywords:
- Database element
ms.assetid: 2ded06c4-4eaf-4ccb-a416-41ee51ced8bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5861be2ad0f5975ef5b95c3f4b077a065b560e02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171962"
---
# <a name="database-element-xmla"></a>Database 要素 (XMLA)
  親によって表されるディメンションを含むデータベースを識別する[オブジェクト](object-element-dimension-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object>  
   ...  
   <Database>...</Database>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Object](object-element-dimension-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Database` 要素は、`Object` 要素によって表されるディメンションを含んでいる Analysis Services データベースの名前を含むオブジェクト識別子です。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;XMLA&#41;](cube-element-xmla.md)   
 [ディメンション要素&#40;XMLA&#41;](dimension-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
