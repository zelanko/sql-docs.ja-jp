---
title: UpdateCells 要素 (XMLA) |Microsoft Docs
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
- UpdateCells Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.updatecells
- urn:schemas-microsoft-com:xml-analysis#UpdateCells
- http://schemas.microsoft.com/analysisservices/2003/engine#UpdateCells
helpviewer_keywords:
- UpdateCells command
ms.assetid: 18336a35-8a46-4532-9ee7-71828b2982af
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05b3b1dae8f409f367a88b696accb77484304b4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219982"
---
# <a name="updatecells-element-xmla"></a>UpdateCells 要素 (XMLA)
  書き込み許可キューブ内のセルを更新します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <UpdateCells>  
      <Cell>...</Cell>  
   </UpdateCells>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[たとえば、マトリックスでは、列ヘッダーに並べ替えボタンを追加してマトリックスにバインドされているデータセットの名前として、コンテナー スコープを指定します。](../xml-elements-properties/cell-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `UpdateCells` コマンドは、セルの書き戻しをサポートするキューブ内のセルを更新します。  
  
 セルの更新の詳細については、「[セルの更新 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Drop 要素&#40;XMLA&#41;](drop-element-xmla.md)   
 [要素を挿入&#40;XMLA&#41;](insert-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](update-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
