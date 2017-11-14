---
title: "ClrAssembly データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ClrAssembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f120b0476b1615db1be21387c641d370cf72f8fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="clrassembly-data-type-assl"></a>ClrAssembly データ型 (ASSL)
  表す派生データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリに関連付けられている、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)または[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし (抽象型)|  
|子要素|[ファイル](../../../analysis-services/scripting/collections/files-element-assl.md)、 [PermissionSet](../../../analysis-services/scripting/properties/permissionset-element-assl.md)|  
|派生要素|参照してください[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)([アセンブリ](../../../analysis-services/scripting/collections/assemblies-element-assl.md)のコレクション[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)または[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 **ClrAssembly**要素には、再作成に必要なファイルが含まれています、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリでは、いずれかのインスタンスに関連付けられている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]またはのインスタンス上の特定のデータベース[!INCLUDE[ssAS](../../../includes/ssas-md.md)]、だけでなく、アセンブリを実行するために必要なアクセス許可。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ClrAssembly>します。  
  
## <a name="see-also"></a>参照  
 [File 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [ClrAssemblyFile データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [データ要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [ComAssembly データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

