---
title: DataBlock データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7ef74279d2430df004ae00429f559ceb9a5c174e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="datablock-data-type-assl"></a>DataBlock データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  バイナリ コンテンツを格納するために使用するデータ ブロックのコレクションを表すプリミティブ データ型を定義、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)要素。  
  
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
|子要素|[ブロック](../../../analysis-services/scripting/collections/blocks-element-assl.md)|  
|派生要素|[データ](../../../analysis-services/scripting/objects/data-element-assl.md)要素の[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)型 ([ファイル](../../../analysis-services/scripting/collections/files-element-assl.md)のコレクション[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)型)|  
  
## <a name="see-also"></a>参照  
 [Assembly 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [File 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Block 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
