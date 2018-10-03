---
title: ManagedProvider 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ManagedProvider Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ManagedProvider element
ms.assetid: ed5a1077-20a4-40b9-b62d-0db0d53b9624
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7b29b4db3d2acf34e684d89588ef5f1e2a935aa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101632"
---
# <a name="managedprovider-element-assl"></a>ManagedProvider 要素 (ASSL)
  派生した要素で使用されるマネージ プロバイダーの名前を含む、 [DataSource](../data-type/datasource-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSource>  
   ...  
   <ManagedProvider>...</ManagedProvider>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSource](../data-type/datasource-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 データ ソースでマネージド プロバイダーが使用される場合、`ManagedProvider` 要素にはマネージド プロバイダーの名前が格納されます。  
  
## <a name="see-also"></a>関連項目  
 [要素名を指定&#40;ASSL&#41;](name-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
