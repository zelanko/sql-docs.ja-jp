---
title: Subscribe 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Subscribe Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords:
- Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 47425fd75c42d70ad98172eee2070bdcb9b2db45
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="subscribe-element-xmla"></a>Subscribe 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]トレースをサブスクライブし、トレース イベントが含まれている行セットを返す、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **購読**コマンドをサブスクライブし、ストリームでは、指定されたトレースから行セットを返します上、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 トレース以外のオブジェクトを **Object** 要素内で指定した場合、エラーが発生します。  
  
 場合、**オブジェクト**要素が指定されていないセッション トレースを定義およびにサブスクライブしている場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 セッション トレースは、トレース イベントの固定されたセットを現在のセッションから返します。  
  
 クライアント アプリケーションへの接続を閉じた場合、このコマンドによって返される行セット ストリームは終了、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、またはセッションを**購読**コマンドが実行が終了します。  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
