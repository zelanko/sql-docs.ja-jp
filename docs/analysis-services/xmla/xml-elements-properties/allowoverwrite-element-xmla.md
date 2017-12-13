---
title: "AllowOverwrite 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: AllowOverwrite Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.allowoverwrite
- urn:schemas-microsoft-com:xml-analysis#EndSession
helpviewer_keywords: AllowOverwrite element
ms.assetid: e7e92481-5f29-47f2-9efd-4e5e60c002bb
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7e13ee21a956848f5e8da9b203af42d3f42d07ce
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="allowoverwrite-element-xmla"></a>AllowOverwrite 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]決定するかどうか、親[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)または[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンドは、ターゲット ファイルまたはデータベースを上書きしようとしています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <AllowOverwrite>...</AllowOverwrite>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **バックアップ**コマンド、 **AllowOverwrite**要素は、コマンドがで指定されたバックアップ ファイルを上書きできるかどうかを判断、**ファイル**要素。  
  
 **復元**、要素、 **AllowOverwrite**要素は、コマンドが上書きできるかどうかを判断、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で指定されたデータベース**DatabaseName**要素。  
  
## <a name="see-also"></a>参照  
 [DatabaseName 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/databasename-element-xmla.md)   
 [File 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
