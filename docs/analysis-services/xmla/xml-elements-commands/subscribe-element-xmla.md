---
title: Subscribe 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f784cbe3c33eb6b2587b7b535668e793fac3b138
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973074"
---
# <a name="subscribe-element-xmla"></a>Subscribe 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  トレースをサブスクライブし、Analysis Services インスタンスからトレース イベントを含む行セットを返します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **購読**コマンドをサブスクライブして、ストリーム指定されたトレースからの行セットのバックアップで、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 トレース以外のオブジェクトを **Object** 要素内で指定した場合、エラーが発生します。  
  
 場合、**オブジェクト**要素が指定されていない場合、セッション トレースが定義され、オンにサブスクライブしている、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 セッション トレースは、トレース イベントの固定されたセットを現在のセッションから返します。  
  
 クライアント アプリケーションへの接続を終了した場合、このコマンドによって返される行セット ストリームは終了、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、またはセッション、**購読**コマンドを実行が終了します。  
  
## <a name="see-also"></a>参照
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
