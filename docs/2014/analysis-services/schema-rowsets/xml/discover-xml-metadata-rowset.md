---
title: DISCOVER_XML_METADATA 行セット |Microsoft ドキュメント
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
- DISCOVER_XML_METADATA
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4452408b36fe50300277d0d0f8e076357403539f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177187"
---
# <a name="discoverxmlmetadata-rowset"></a>DISCOVER_XML_METADATA 行セット
  要求されたオブジェクトについて記述する XML ドキュメントを返します。 返される行セットは、必ず 1 行および 1 列で構成されます。  
  
 呼び出す場合は、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッドを`DISCOVER_XML_METATDATA`の列挙値に、 [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)要素、`Discover`メソッドを返します。、`DISCOVER_XML_METATDATA`行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_XML_METADATA` 行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`METADATA`|`DBTYPE_WSTR`||制限によって要求されたオブジェクトについて記述する XML ドキュメント。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  `DISCOVER_XML_METADATA` 行セットに対して、SELECT コマンド構文を使用してクエリを実行することはできません。 ただし、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> を使用して `DISCOVER_XML_METADATA` 行セットにクエリを実行することはできます。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_XML_METADATA`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`DatabaseID`|`DBTYPE_WSTR`|任意。|  
|`DimensionID`|`DBTYPE_WSTR`|任意。|  
|`CubeID`|`DBTYPE_WSTR`|任意。|  
|`MeasureGroupID`|`DBTYPE_WSTR`|任意。|  
|`PartitionID`|`DBTYPE_WSTR`|任意。|  
|`PerspectiveID`|`DBTYPE_WSTR`|任意。|  
|`DimensionPermissionID`|`DBTYPE_WSTR`|任意。|  
|`RoleID`|`DBTYPE_WSTR`|任意。|  
|`DatabasePermissionID`|`DBTYPE_WSTR`|任意。|  
|`MiningModelID`|`DBTYPE_WSTR`|任意。|  
|`MiningModelPermissionID`|`DBTYPE_WSTR`|任意。|  
|`DataSourceID`|`DBTYPE_WSTR`|任意。|  
|`MiningStructureID`|`DBTYPE_WSTR`|任意。|  
|`AggregationDesignID`|`DBTYPE_WSTR`|任意。|  
|`TraceID`|`DBTYPE_WSTR`|任意。|  
|`MiningStructurePermissionID`|`DBTYPE_WSTR`|任意。|  
|`CubePermissionID`|`DBTYPE_WSTR`|任意。|  
|`AssemblyID`|`DBTYPE_WSTR`|任意。|  
|`MdxScriptID`|`DBTYPE_WSTR`|任意。|  
|`DataSourceViewID`|`DBTYPE_WSTR`|任意。|  
|`DataSourcePermissionID`|`DBTYPE_WSTR`|任意。|  
|`ObjectExpansion`|`DBTYPE_WSTR`|任意。|  
  
 制限、`ObjectExpansion`のすべての主要なオブジェクトがある[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 クライアントは通常、DDL を返す対象となる OLAP オブジェクトを記述するために制限を使用します。また、返された DDL の拡張度を定義するために `ObjectExpansion` 制限を使用します。 次の表は、の列挙値が許可されているかどうかを示す[Alter 要素&#40;XMLA&#41; ](../../xmla/xml-elements-commands/alter-element-xmla.md)コマンド。  
  
|列挙値|説明|  
|-----------------------|-----------------|  
|`ReferenceOnly`|要求されたオブジェクトおよび子孫であるすべての主要なオブジェクトに対して要求された名前、ID、タイムスタンプ、および状態だけを再帰的に返します。|  
|`ObjectProperties`|含まれるオブジェクト (含まれる展開済みのマイナー オブジェクトを含む) に関係なく、要求されたオブジェクトを展開します。|  
|`ExpandObject`|同じ*ObjectProperties*名前、ID、および含まれる主要なオブジェクトのタイムスタンプも返されます。|  
|`ExpandFull`|要求されたオブジェクトを、含まれるすべてのオブジェクトの一番下まで再帰的に完全に展開します。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  