---
title: DISCOVER_XML_METADATA 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a01f73cb3ef8647f179143e4be8b71f9dceee755
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discoverxmlmetadata-rowset"></a>DISCOVER_XML_METADATA 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  要求されたオブジェクトについて記述する XML ドキュメントを返します。 返される行セットは、必ず 1 行および 1 列で構成されます。  
  
 呼び出す場合は、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドを**DISCOVER_XML_METATDATA**の列挙値に、 [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)要素、 **Discover**メソッドを返します、 **DISCOVER_XML_METATDATA**行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_XML_METADATA**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**METADATA**|**DBTYPE_WSTR**||制限によって要求されたオブジェクトについて記述する XML ドキュメント。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  **DISCOVER_XML_METADATA** SELECT コマンド構文を使用して行セットをクエリすることはできません。 ただし、 **DISCOVER_XML_METADATA**を使用してクエリできる行セット<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_XML_METADATA**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**DatabaseID**|**DBTYPE_WSTR**|省略可。|  
|**DimensionID**|**DBTYPE_WSTR**|省略可。|  
|**CubeID**|**DBTYPE_WSTR**|省略可。|  
|**MeasureGroupID**|**DBTYPE_WSTR**|省略可。|  
|**PartitionID**|**DBTYPE_WSTR**|省略可。|  
|**PerspectiveID**|**DBTYPE_WSTR**|省略可。|  
|**DimensionPermissionID**|**DBTYPE_WSTR**|省略可。|  
|**RoleID**|**DBTYPE_WSTR**|省略可。|  
|**DatabasePermissionID**|**DBTYPE_WSTR**|省略可。|  
|**MiningModelID**|**DBTYPE_WSTR**|省略可。|  
|**MiningModelPermissionID**|**DBTYPE_WSTR**|省略可。|  
|**DataSourceID**|**DBTYPE_WSTR**|省略可。|  
|**MiningStructureID**|**DBTYPE_WSTR**|省略可。|  
|**AggregationDesignID**|**DBTYPE_WSTR**|省略可。|  
|**TraceID**|**DBTYPE_WSTR**|省略可。|  
|**MiningStructurePermissionID**|**DBTYPE_WSTR**|省略可。|  
|**CubePermissionID**|**DBTYPE_WSTR**|省略可。|  
|**AssemblyID**|**DBTYPE_WSTR**|省略可。|  
|**MdxScriptID**|**DBTYPE_WSTR**|省略可。|  
|**DataSourceViewID**|**DBTYPE_WSTR**|省略可。|  
|**DataSourcePermissionID**|**DBTYPE_WSTR**|省略可。|  
|**ObjectExpansion**|**DBTYPE_WSTR**|省略可。|  
  
 制限、 **ObjectExpansion**のすべての主要なオブジェクトがある[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 クライアントを使用して、DDL を返される OLAP オブジェクトを記述する制限を使用する通常、 **ObjectExpansion**返された ddl の拡張度を定義する制限。 次の表は、の列挙値が許可されているかどうかを示す[Alter 要素&#40;XMLA&#41; ](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)コマンド。  
  
|列挙値|Description|  
|-----------------------|-----------------|  
|**ReferenceOnly**|要求されたオブジェクトおよび子孫であるすべての主要なオブジェクトに対して要求された名前、ID、タイムスタンプ、および状態だけを再帰的に返します。|  
|**ObjectProperties**|含まれるオブジェクト (含まれる展開済みのマイナー オブジェクトを含む) に関係なく、要求されたオブジェクトを展開します。|  
|**ExpandObject**|同じ*ObjectProperties*名前、ID、および含まれる主要なオブジェクトのタイムスタンプも返されます。|  
|**ExpandFull**|要求されたオブジェクトを、含まれるすべてのオブジェクトの一番下まで再帰的に完全に展開します。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
