---
title: "Analysis Services オブジェクトの種類のコードにトレースで使用される |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e4119db1-4a41-4335-9b33-f1ea95564300
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 09c8d0a538d539c54e304d220566345a96a5e2f1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="analysis-services-object-type-codes-used-in-traces"></a>トレースで使用される Analysis Services オブジェクトの種類のコード
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]このページには、Analysis Services データ モデル内の各オブジェクトのオブジェクトの種類 (6 桁の数字) が一覧表示されます。 これらのコードは、トレース ログに表示され、特定のロックに関連付けられているオブジェクトの種類を識別するために使用されます。 たとえば、データベースでのロックのタイムアウトは、オブジェクトの種類が 100002 で、これはデータベース オブジェクトの種類を示します。  
  
> [!NOTE]  
>  トレース ログに実際に表示されるよりも多くのコードが、以下に一覧表示されています。 以下の一覧はすべてのオブジェクトの種類のコードの包括的な一覧ですが、ロックを取得するオブジェクトのみがトレース ログにオブジェクトの種類のコードを表示します。  
  
## <a name="object-type-reference"></a>オブジェクトの種類のリファレンス  
  
|オブジェクトの種類|オブジェクト名です。|  
|-----------------|-----------------|  
|100000|[サーバー]|  
|100001|Command|  
|100002|データベース|  
|100003|DataSource|  
|100004|DatabasePermission|  
|100005|ロール|  
|100006|[ディメンション]|  
|100007|DimensionAttribute|  
|100008|階層|  
|100009|レベル|  
|100010|Cube|  
|100011|CubePermission|  
|100012|CubeDimension|  
|100013|CubeAttribute|  
|100014|CubeHierarchy|  
|100016|[MeasureGroup]|  
|100017|MeasureGroupDimension|  
|100018|MeasureGroupAttribute|  
|100020|[メジャー]|  
|100021|パーティション|  
|100025|AggregationDesign|  
|100026|AggregationDesignDimension|  
|100027|AggregationDesignAttribute|  
|100028|[集計]|  
|100029|AggregationDimension|  
|100030|AggregationAttribute|  
|100032|MiningStructure|  
|100033|MiningStructureColumn|  
|100037|MiningModel|  
|100038|MiningModelColumn|  
|100039|AlgorithmParameter|  
|100041|MiningModelPermission|  
|100042|DimensionPermission|  
|100043|MiningStructurePermission|  
|100044|アセンブリ|  
|100045|DatabaseRole|  
|100046|AttributePermission|  
|100047|CubeAttributePermission|  
|100048|CellPermission|  
|100049|CubeDimensionPermission|  
|100050|トレース|  
|100051|ServerAssembly|  
|100052|CubeAssembly|  
|100053|Command|  
|100054|KPI (KPI)|  
|100055|DataSourceView|  
|100056|Perspective|  
|100100|CommandCollection|  
|100101|DatabaseCollection|  
|100102|DataSourceCollection|  
|100103|DatabasePermission|  
|100104|RoleCollection|  
|100105|DimensionCollection|  
|100106|DimensionAttributeCollection|  
|100107|HierarchyCollection|  
|100108|LevelCollection|  
|100109|CubeCollection|  
|100110|CubePermissionCollection|  
|100111|CubeDimensionCollection|  
|100112|CubeAttributeCollection|  
|100113|CubeHierarchyCollection|  
|100115|MeasureGroupCollection|  
|100116|MeasureGroupDimensionCollection|  
|100117|MeasureGroupAttributeCollection|  
|100119|MeasureCollection|  
|100120|PartitionCollection|  
|100124|AggregationDesignCollection|  
|100125|AggregationDesignDimensionCollection|  
|100126|AggregationDesignAttributeCollection|  
|100127|AggregationCollection|  
|100128|AggregationDimensionCollection|  
|100129|AggregationAttributeCollection|  
|100131|MiningStructureCollection|  
|100132|MiningStructureColumnCollection|  
|100136|MiningModelCollection|  
|100137|MiningModelColumnCollection|  
|100138|AlgorithmParameterCollection|  
|100140|MiningModelPermissionCollection|  
|100141|DimensionPermissionCollection|  
|100142|MiningStructurePermissionCollection|  
|100143|AssemblyCollection|  
|100144|DatabaseRoleCollecction|  
|100145|AttributePermissionCollection|  
|100146|CubeAttributePermissionCollection|  
|100147|CellPermissionCollection|  
|100148|CubeDimensionPermissionCollection|  
|100149|TraceCollection|  
|100150|ServerAssemblyCollection|  
|100151|CubeAssemblyCollection|  
|100152|CommandCollection|  
|100153|KpiCollection|  
|100154|DataSourceViewCollection|  
|100155|PerspectiveCollection|  
  
  
