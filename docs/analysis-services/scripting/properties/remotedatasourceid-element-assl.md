---
title: "RemoteDatasourceID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- RemoteDatasourceID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RemoteDatasourceID
helpviewer_keywords:
- RemoteDatasourceID element
ms.assetid: 2eaf0b9c-8c2d-4dc6-9bad-1db70a4b04b1
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eade7b321c47c5add6a5302f5c015ed6484c2b5f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="remotedatasourceid-element-assl"></a>RemoteDatasourceID 要素 (ASSL)
  インスタンスを指す OLAP データ ソースの識別子 (ID) を指定[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]リモート パーティションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Partition>  
      ...  
   <RemoteDatasourceID>...</RemoteDatasourceID>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 場合**RemoteDatasourceID**が null で、パーティションはローカルです。  
  
 親に対応する要素**RemoteDatasourceID**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Partition>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

