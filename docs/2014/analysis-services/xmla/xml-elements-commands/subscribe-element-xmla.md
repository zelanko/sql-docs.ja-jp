---
title: Subscribe 要素 (XMLA) |Microsoft ドキュメント
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
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 94caa1327febf0c7fd5a489c7558ea793977d027
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082844"
---
# <a name="subscribe-element-xmla"></a>Subscribe 要素 (XMLA)
  トレースをサブスクライブし、トレース イベントが含まれている行セットを返す、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
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
 `Subscribe`コマンドをサブスクライブし、ストリームでは、指定されたトレースから行セットを返します上、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 トレース以外のオブジェクトで指定したが、`Object`要素、エラーが発生します。  
  
 `Object` 要素が指定されていない場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに対するセッション トレースが定義され、それがサブスクライブされます。 セッション トレースは、トレース イベントの固定されたセットを現在のセッションから返します。  
  
 クライアント アプリケーションへの接続を閉じた場合、このコマンドによって返される行セット ストリームは終了、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、またはセッションを`Subscribe`コマンドが実行が終了します。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  