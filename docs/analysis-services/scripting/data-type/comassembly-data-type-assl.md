---
title: "ComAssembly データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ComAssembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e519b7f204e5fe258222a48161dc9032ccc826ac
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="comassembly-data-type-assl"></a>ComAssembly データ型 (ASSL)
  関連付けられた COM ライブラリを表す派生データ型を定義、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)または[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、 [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]では、COM アセンブリが推奨されていません。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ComAssembly>  
      <!-- The following elements extend Assembly -->  
   <Source>...</Source>  
</ComAssembly>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ソース](../../../analysis-services/scripting/properties/source-element-comassembly-assl.md)|  
|派生要素|参照してください[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)([アセンブリ](../../../analysis-services/scripting/collections/assemblies-element-assl.md)のコレクション[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)または[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 **ComAssembly**要素のインスタンスに関連付けられた COM ライブラリ (完全修飾ファイル名またはプログラム識別子) の参照を含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]または特定インスタンス上のデータベース[!INCLUDE[ssAS](../../../includes/ssas-md.md)]です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ComAssembly>します。  
  
## <a name="see-also"></a>参照  
 [ClrAssembly データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

