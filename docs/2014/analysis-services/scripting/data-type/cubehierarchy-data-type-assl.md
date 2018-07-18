---
title: CubeHierarchy データ型 (ASSL) |Microsoft Docs
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
- CubeHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeHierarchy
helpviewer_keywords:
- CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0d719b6c841b27df473599514dc12c4e90644610
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176199"
---
# <a name="cubehierarchy-data-type-assl"></a>CubeHierarchy データ型 (ASSL)
  に関する情報を表すプリミティブ データ型を定義、[階層](../objects/hierarchy-element-assl.md)内の要素を[キューブ](../objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|子要素|[注釈](../collections/annotations-element-assl.md)、[有効になっている](../properties/enabled-element-assl.md)、 [HierarchyID](../properties/id-element-assl.md)、[名前](../properties/name-element-assl.md)、 [OptimizedState](../properties/state-element-assl.md)、[表示](../properties/visible-element-assl.md)|  
|派生要素|[階層](../objects/hierarchy-element-assl.md)([階層](../collections/hierarchies-element-assl.md)のコレクション[CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>コメント  
 このデータ型には制限はなく、いずれの配置モード (0 - 多次元およびデータ マイニング、1 - SharePoint、および 2 - テーブル) でも使用できます。  
  
 [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)]、*有効*にプロパティを設定することはできません`False`の*CubeHierarchy*します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeHierarchy>します。  
  
## <a name="see-also"></a>参照  
 [Discover メソッド&#40;XMLA&#41;](../../xmla/xml-elements-methods-discover.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
