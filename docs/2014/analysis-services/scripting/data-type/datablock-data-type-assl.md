---
title: DataBlock データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DataBlock Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataBlock
helpviewer_keywords:
- DataBlock data type
ms.assetid: 4192b388-613a-472b-881c-f9c02215aa81
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 167af587de6f06d283ec29f8afbc0fedb2ebc99e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211962"
---
# <a name="datablock-data-type-assl"></a>DataBlock データ型 (ASSL)
  バイナリ コンテンツを格納するために使用するデータ ブロックのコレクションを表すプリミティブ データ型を定義、 [ClrAssemblyFile](clrassemblyfile-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ブロック](../collections/blocks-element-assl.md)|  
|派生要素|[データ](../objects/data-element-assl.md)要素の[ClrAssemblyFile](clrassemblyfile-data-type-assl.md)型 ([ファイル](../collections/files-element-assl.md)のコレクション[ClrAssembly](assembly-data-type-assl.md)型)|  
  
## <a name="see-also"></a>参照  
 [Assembly 要素&#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [要素が&#40;ASSL&#41;](../objects/file-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
