---
title: DataBlock データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 656ed967d0e306668203abd46a4b2525655e0f61
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032043"
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
  
  
