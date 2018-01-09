---
title: "Type 要素 (ClrAssemblyFile) (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element (ClrAssemblyFile)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0f22616627c6eb7f2a10edfde1aec989887e92dc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-clrassemblyfile-assl"></a>Type 要素 (ClrAssemblyFile) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]属しているファイルの 1 つのファイルの種類を指定します、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アセンブリ。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ClrAssemblyFile>  
      ...  
      <Type>...</Type>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*メイン*|アセンブリのメイン ファイルであるファイルを指定します。|  
|*依存します。*|アセンブリの依存ファイルであるファイルを指定します。|  
|*デバッグ*|デバック情報を含んでいるファイルを指定します。|  
  
 許可される値に対応する列挙**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFileType>します。  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [File 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Files 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [ClrAssembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Assembly 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Assemblies 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
