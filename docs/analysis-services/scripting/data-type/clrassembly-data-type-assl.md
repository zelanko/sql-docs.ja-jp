---
title: ClrAssembly データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6fb3493fc7add4ece9ef2d5acacd772d5911ebd
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037083"
---
# <a name="clrassembly-data-type-assl"></a>ClrAssembly データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|派生要素|「 [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) 」を参照 ([Database](../../../analysis-services/scripting/collections/assemblies-element-assl.md) または [Server](../../../analysis-services/scripting/objects/database-element-assl.md) の [Assemblies](../../../analysis-services/scripting/objects/server-element-assl.md)コレクション)|  
  
## <a name="remarks"></a>解説  
 **ClrAssembly**要素には、再作成に必要なファイルが含まれています、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリでは、いずれかのインスタンスに関連付けられている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]またはのインスタンス上の特定のデータベース[!INCLUDE[ssAS](../../../includes/ssas-md.md)]、だけでなく、アセンブリを実行するために必要なアクセス許可。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ClrAssembly>します。  
  
## <a name="see-also"></a>参照  
 [File 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [ClrAssemblyFile データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [データ要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [ComAssembly データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
