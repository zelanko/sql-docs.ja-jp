---
title: ClrAssembly データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ClrAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9171832bac6653e7c1d86915ae006c65022668a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159252"
---
# <a name="clrassembly-data-type-assl"></a>ClrAssembly データ型 (ASSL)
  表す派生データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリに関連付けられている、[データベース](../objects/database-element-assl.md)または[Server](../objects/server-element-assl.md)要素  
  
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
|基本データ型|[アセンブリ](../objects/assembly-element-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし (抽象型)|  
|子要素|[ファイル](../collections/files-element-assl.md)、 [PermissionSet](../properties/permissionset-element-assl.md)|  
|派生要素|参照してください[アセンブリ](../objects/assembly-element-assl.md)([アセンブリ](../collections/assemblies-element-assl.md)のコレクション[データベース](../objects/database-element-assl.md)または[Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 `ClrAssembly`要素には再作成に必要なファイルが含まれています、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリでは、いずれかのインスタンスに関連付けられている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]またはインスタンス上の特定のデータベースと[!INCLUDE[ssAS](../../../includes/ssas-md.md)]、だけでなくアセンブリを実行するアクセス許可が必要です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ClrAssembly>します。  
  
## <a name="see-also"></a>参照  
 [要素が&#40;ASSL&#41;](../objects/file-element-assl.md)   
 [ClrAssemblyFile データ型&#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)   
 [データ要素&#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock データ型&#40;ASSL&#41;](datablock-data-type-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../objects/block-element-assl.md)   
 [ComAssembly データ型&#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
