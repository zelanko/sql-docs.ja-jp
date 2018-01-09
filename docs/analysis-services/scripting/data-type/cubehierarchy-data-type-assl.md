---
title: "CubeHierarchy データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CubeHierarchy Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CubeHierarchy
helpviewer_keywords: CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6ed9177da67bf17a4be9cabf49404bd1b51a31de
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cubehierarchy-data-type-assl"></a>CubeHierarchy データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]に関する情報を表すプリミティブ データ型を定義、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)内の要素、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[有効になっている](../../../analysis-services/scripting/properties/enabled-element-assl.md)、 [HierarchyID](../../../analysis-services/scripting/properties/hierarchyid-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [OptimizedState](../../../analysis-services/scripting/properties/optimizedstate-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
|派生要素|[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)([階層](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)のコレクション[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 このデータ型には制限はなく、いずれの配置モード (0 - 多次元およびデータ マイニング、1 - SharePoint、および 2 - テーブル) でも使用できます。  
  
 以降、および SQL Server 2016 Analysis Services、*有効*プロパティに設定することはできません**False**の*CubeHierarchy*です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeHierarchy>します。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を検出します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
