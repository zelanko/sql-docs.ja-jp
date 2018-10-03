---
title: 要素 (XMLA) の処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Process Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Process
- http://schemas.microsoft.com/analysisservices/2003/engine#Process
- microsoft.xml.analysis.process
helpviewer_keywords:
- Process command
ms.assetid: 886fd480-c0e6-4c9b-b65e-da47f874d938
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec706973bca433a64d6a27201264509ade5ce773
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149462"
---
# <a name="process-element-xmla"></a>Process 要素 (XMLA)
  上のオブジェクトを処理する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Process>  
      <Type>...</Type>  
      <Object>...</Object>  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <WriteBackTableCreation>...</WriteBackTableCreation>  
   </Process>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[バインド](../xml-elements-properties/bindings-element-xmla.md)、 [DataSource](../xml-elements-properties/source-element-xmla.md)、 [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md)、 [ErrorConfiguration](../xml-elements-properties/errorconfiguration-element-xmla.md)、[オブジェクト](../xml-elements-properties/object-element-xmla.md)、[型要素&#40;XMLA&#41;](../xml-elements-properties/type-element-xmla.md)、 [WriteBackTableCreation](../xml-elements-properties/writebacktablecreation-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 オブジェクトの処理の詳細については、次を参照してください。[オブジェクトの処理&#40;XMLA&#41;](../xml-elements-objects.md)します。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
