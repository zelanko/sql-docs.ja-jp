---
title: DataSource データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSource Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSource data type
ms.assetid: 05e8de8d-452d-4128-98a6-4437df227fec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0eecebc417a1ddf33f00cdaf5977ca8d3297aca7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069362"
---
# <a name="datasource-data-type-assl"></a>DataSource データ型 (ASSL)
  内のデータ ソースを表す抽象プリミティブ データ型を定義、[データベース](../objects/database-element-assl.md)要素。  
  
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
|派生データ型|[RelationalDataSource](datasource-data-type-assl.md)、 [OlapDataSource](olapdatasource-data-type-assl.md)、 [PushedDataSource](pusheddatasource-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [ConnectionString](../properties/connectionstring-element-assl.md)、 [ConnectionStringSecurity](../properties/connectionstringsecurity-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [DataSourcePermission](../collections/datasourcepermissions-element-assl.md)、[説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [ImpersonationInfo](../properties/impersonationinfo-element-assl.md)、[分離](../properties/isolation-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [ManagedProvider](../properties/managedprovider-element-assl.md)、 [MaxActiveConnections](../properties/maxactiveconnections-element-assl.md)、[名前](../properties/name-element-assl.md)、[タイムアウト](../properties/timeout-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 不一致バインドを定義する場合、`Name` 要素はオプションです。 `Name` 要素を指定する必要がない場合は、キューブやパーティションなどのバインド内にデータ ソースを定義できます。 `Database` 要素に含まれているデータ ソースの場合、`Name` は必須要素です。  
  
 使用できるデータ ソースの詳細については、「 [多次元モデルのデータ ソース](../../multidimensional-models/data-sources-in-multidimensional-models.md)」を参照してください。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DataSource>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
