---
title: Resultset データ型 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Resultset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a34b99aa63608faafa42d94aaf8938f86bb3894c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205492"
---
# <a name="resultset-data-type-xmla"></a>Resultset データ型 (XMLA)
  返されるデータを表す抽象プリミティブ データ型を定義、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッドの呼び出し。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-: 結果セットの分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[MDDataSet](mddataset-data-type-xmla.md)、 [olapxmla_EmptyResult](emptyresult-data-type-xmla.md)、[行セット](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[例外](../xml-elements-properties/exception-element-xmla.md)、[メッセージ](../xml-elements-properties/messages-element-xmla.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Resultset` データ型は自己記述型 XML 結果セットで、返される情報の種類に応じてスキーマとデータの両方を格納することができます。  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
