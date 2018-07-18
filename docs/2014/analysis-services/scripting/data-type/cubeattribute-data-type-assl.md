---
title: CubeAttribute データ型 (ASSL) |Microsoft Docs
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
- CubeAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b1df72c234fe7835d739e2b1835b01041aa9cbe6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319352"
---
# <a name="cubeattribute-data-type-assl"></a>CubeAttribute データ型 (ASSL)
  関連付けられている属性を表すプリミティブ データ型を定義、[キューブ](../objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[AggregationUsage](../properties/aggregationusage-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、 [AttributeHierarchyEnabled](../properties/enabled-element-assl.md)、 [AttributeHierarchyOptimizedState](../properties/state-element-assl.md)、 [AttributeHierarchyVisible](../properties/visible-element-assl.md)、 [AttributeID](../properties/id-element-assl.md)|  
|派生要素|[属性](../objects/attribute-element-assl.md)([属性](../collections/attributes-element-assl.md)のコレクション[CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>コメント  
 *AttributeHierarchyOptimizedState* DeploymentMode 構成プロパティの値 1 または 2 (SharePoint モードまたは表形式モード、PowerPivot とテーブル モデル データベースを実行するために使用) でサービスを実行するときに、要素がサポートされていません。  
  
 階層のレベルとして属性を追加することはできませんと、プロパティ*AtttributeHierarchyEnabled*FALSE に設定されている DeploymentMode 1 または 2 (SharePoint または表形式サーバー モード) インスタンスが動作しているとします。  
  
 属性、 [CubeDimension](dimension-data-type-assl.md)要素に明示的に含まれていない、[属性](../collections/attributes-element-assl.md)割り当てられている既定値を持つコレクションの一部をコレクションになります。 によって返される属性、属性を追加するコレクションの後、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッド。  
  
 [AggregationUsage](../properties/aggregationusage-element-assl.md)要素コントロール方法[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]自動的に、属性の集計をデザインします。 `AggregationUsage` 要素では、キューブに対して手動で作成する集計が制限されません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeAttribute>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
