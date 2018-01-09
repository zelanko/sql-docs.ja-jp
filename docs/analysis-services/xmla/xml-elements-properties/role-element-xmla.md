---
title: "Role 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 2b851ad5-cc46-4a2e-8873-d8556faca809
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dee3f366a21d19d1e57dd65a3f1a0397ca3b9ac4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="role-element--xmla"></a>Role 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]親によって使用される一対多リレーションシップの一方の端を識別[RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEnd  
   ...  
   <Role>...</Role>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|基数|1: 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
  
