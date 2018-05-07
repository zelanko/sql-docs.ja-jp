---
title: DataSource データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92d716c8106d5ae3d093a5206b913acf85c17da7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="datasource-data-type-assl"></a>DataSource データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  内のデータ ソースを表す抽象プリミティブ データ型を定義、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSource>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ManagedProvider>...</ManagedProvider>  
   <ConnectionString>...</ConnectionString>  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Isolation>...</Isolation>  
   <MaxActiveConnections>...</MaxActiveConnections>  
   <Description>...</Description>  
   <Timeout>...</Timeout>  
   <Annotations>...</Annotations>  
   <DataSourcePermission>...</DataSourcePermission>  
</DataSource>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[RelationalDataSource](../../../analysis-services/scripting/data-type/relationaldatasource-data-type-assl.md)、 [OlapDataSource](../../../analysis-services/scripting/data-type/olapdatasource-data-type-assl.md)、 [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [ConnectionString](../../../analysis-services/scripting/properties/connectionstring-element-assl.md)、 [ConnectionStringSecurity](../../../analysis-services/scripting/properties/connectionstringsecurity-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [DataSourcePermission](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)、[分離](../../../analysis-services/scripting/properties/isolation-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [ManagedProvider](../../../analysis-services/scripting/properties/managedprovider-element-assl.md)、 [MaxActiveConnections](../../../analysis-services/scripting/properties/maxactiveconnections-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[タイムアウト](../../../analysis-services/scripting/properties/timeout-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 行外のバインディングを定義するときに、**名前**要素は省略可能です。 指定する必要がなく、**名前**要素には、キューブやパーティションなどのバインド内で定義するデータ ソースができるようにします。 含まれているデータ ソースに対して、**データベース**要素、**名前**の必要な要素は、します。  
  
 使用できるデータ ソースの詳細については、「 [多次元モデルのデータ ソース](../../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)」を参照してください。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DataSource>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
