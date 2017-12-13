---
title: "Source 要素 (Synchronize) (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Source Element (Synchronize)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Source
- http://schemas.microsoft.com/analysisservices/2003/engine#Source
- microsoft.xml.analysis.source
helpviewer_keywords: Source element
ms.assetid: 0a857f91-771f-4c5e-8bf7-4bf17442d4df
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9d5d8448c3bd048313435076f66d6f434d3ce552
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="source-element-synchronize-xmla"></a>Source 要素 (Synchronize) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]元の中にターゲット データベースを同期するためにソース データベースを表す、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Synchronize>  
   <Source>  
      <Object>...</Object>  
      <ConnectionString>...</ConnectionString>  
   </Source>  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)、[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **同期**コマンドを使用して、**ソース**への接続を確立し、インスタンス上のデータベースを識別する要素[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]同期に使用します。ターゲット データベース。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
