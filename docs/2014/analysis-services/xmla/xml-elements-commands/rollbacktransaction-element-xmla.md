---
title: RollbackTransaction 要素 (XMLA) |Microsoft Docs
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
- RollbackTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RollbackTransaction
- microsoft.xml.analysis.rollbacktransaction
- urn:schemas-microsoft-com:xml-analysis#RollbackTransaction
helpviewer_keywords:
- RollbackTransaction command
ms.assetid: 40e7dc00-656f-412f-97f0-d05bf7caa196
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eaaf3d92849e0d2ddb7f94686bb30e627d3abcb7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300802"
---
# <a name="rollbacktransaction-element-xmla"></a>RollbackTransaction 要素 (XMLA)
  インスタンスと現在のセッションでトランザクションをロールバック[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
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
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `RollbackTransaction` コマンドは、現在のセッションで、`BeginTransaction` 要素を使用して明示的に定義された、すべてのアクティブなトランザクションをロールバックします。 既存のアクティブなトランザクションがない場合、エラーが発生します。 アクティブなトランザクションが既に存在する場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは現在のセッションのトランザクションの参照カウントを 0 に減らして、すべてのアクティブなトランザクションをロールバックします。  
  
## <a name="see-also"></a>参照  
 [BeginTransaction 要素&#40;XMLA&#41;](begintransaction-element-xmla.md)   
 [Cancel 要素&#40;XMLA&#41;](cancel-element-xmla.md)   
 [CommitTransaction 要素&#40;XMLA&#41;](committransaction-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
