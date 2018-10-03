---
title: ComAssembly データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ComAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cf05a673de90310563cdc5264f61e2da0952450
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133452"
---
# <a name="comassembly-data-type-assl"></a>ComAssembly データ型 (ASSL)
  関連付けられた COM ライブラリを表す派生データ型を定義、 [Server](../objects/server-element-assl.md)または[データベース](../objects/database-element-assl.md)要素。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、[!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)] では、COM アセンブリが非推奨とされました。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
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
|基本データ型|[アセンブリ](../objects/assembly-element-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[Source](../properties/source-element-comassembly-assl.md)|  
|派生要素|参照してください[アセンブリ](../objects/assembly-element-assl.md)([アセンブリ](../collections/assemblies-element-assl.md)のコレクション[データベース](../objects/database-element-assl.md)または[Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 `ComAssembly` 要素は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスに関連付けられた COM ライブラリ、または [!INCLUDE[ssAS](../../../includes/ssas-md.md)] のインスタンス上の特定のデータベースに関連付けられた COM ライブラリへの参照 (完全修飾ファイル名またはプログラム識別子) を格納します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ComAssembly>します。  
  
## <a name="see-also"></a>参照  
 [ClrAssembly データ型&#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
