---
title: "Resultset データ型 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Resultset Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 30d8923c5e3e84c3e2f835caf160902c96c9bf4d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="resultset-data-type-xmla"></a>Resultset データ型 (XMLA)
  返されたデータを表す抽象プリミティブ データ型を定義、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: 結果セット  
  
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
|派生データ型|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)、 [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)、[行セット](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[例外](../../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md)、[メッセージ](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 **Resultset**データ型は自己記述型 XML 結果セットのスキーマと返される情報の種類に応じて、データの両方を含むことができます。  
  
## <a name="see-also"></a>参照  
 [XML データ型 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  

