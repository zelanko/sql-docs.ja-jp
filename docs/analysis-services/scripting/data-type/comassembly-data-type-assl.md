---
title: ComAssembly データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b01a29856bf42d275b1c4d59c9041a9f6f4ab270
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="comassembly-data-type-assl"></a>ComAssembly データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [Server](../../../analysis-services/scripting/objects/server-element-assl.md) 要素または [Database](../../../analysis-services/scripting/objects/database-element-assl.md) 要素に関連付けられた COM ライブラリを表す派生データ型を定義します。  
  
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
|派生要素|「 [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) 」を参照 ([Database](../../../analysis-services/scripting/collections/assemblies-element-assl.md) または [Server](../../../analysis-services/scripting/objects/database-element-assl.md) の [Assemblies](../../../analysis-services/scripting/objects/server-element-assl.md)コレクション)|  
  
## <a name="remarks"></a>解説  
 **ComAssembly**要素のインスタンスに関連付けられた COM ライブラリ (完全修飾ファイル名またはプログラム識別子) の参照を含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]または特定インスタンス上のデータベース[!INCLUDE[ssAS](../../../includes/ssas-md.md)]です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ComAssembly>します。  
  
## <a name="see-also"></a>参照  
 [ClrAssembly データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
