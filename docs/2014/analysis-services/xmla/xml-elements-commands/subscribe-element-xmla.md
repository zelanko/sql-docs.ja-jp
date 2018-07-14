---
title: Subscribe 要素 (XMLA) |Microsoft Docs
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
- Subscribe Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords:
- Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97b473820ee809f5a606e8bb9f30be6e315a2801
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247262"
---
# <a name="subscribe-element-xmla"></a>Subscribe 要素 (XMLA)
  トレースをサブスクライブしからのトレース イベントを含む行セットを返します、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[Object](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Subscribe`コマンドをサブスクライブして、ストリーム指定されたトレースからの行セットのバックアップで、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 トレース以外のオブジェクトで指定したが、`Object`要素、エラーが発生します。  
  
 `Object` 要素が指定されていない場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに対するセッション トレースが定義され、それがサブスクライブされます。 セッション トレースは、トレース イベントの固定されたセットを現在のセッションから返します。  
  
 クライアント アプリケーションへの接続を閉じた場合、このコマンドによって返される行セット ストリームは終了、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、またはセッション、`Subscribe`コマンドを実行が終了します。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
