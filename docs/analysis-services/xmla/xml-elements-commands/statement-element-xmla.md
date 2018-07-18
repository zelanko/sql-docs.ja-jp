---
title: Statement 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49238b50457a586bbf23cc75ee454003c57ac04e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979164"
---
# <a name="statement-element-xmla"></a>Statement 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  クエリまたは送信されるステートメントを含むを使用して、 **Execute** Analysis Services のインスタンスにメソッド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Statement>...</Statement>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **ステートメント**コマンドでクエリまたはステートメントの実行、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は次の言語をサポートします。  
  
-   多次元式 (MDX) (Multidimensional Expressions (MDX))  
  
-   データ マイニング拡張機能 (MDX)  
  
-   構造化照会言語 (SQL) のサブセット  
  
## <a name="see-also"></a>参照
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
