---
title: BeginTransaction 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb4a4dea3658ad03fd6205f9076bd1cb65ca9ba7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038380"
---
# <a name="begintransaction-element-xmla"></a>BeginTransaction 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services のインスタンスと現在のセッションでトランザクションを開始します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <BeginTransaction />  
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
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **BeginTransaction**コマンドは、現在のセッションにアクティブなトランザクションを開始します。 アクティブなトランザクションが既に存在する場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは現在のセッションのトランザクション参照カウントを増やします。 まだ存在しない場合、インスタンスは新しいトランザクションを開始して、現在のセッションの参照カウントを 1 に設定します。 使用して、アクティブなトランザクションを明示的に指定する場合、 **BeginTransaction**コマンドを明示的に指定されたトランザクション内ですべての後続のコマンドが実行されます。  
  
 現在のセッションが終了したときにトランザクションの参照カウントが 0 より大きければ、すべてのアクティブなトランザクションはロールバックされます。  
  
 明示的に指定されたアクティブなトランザクションが現在のセッションに存在しない場合、現在のセッションで発行されるすべてのコマンドは、暗黙的に定義されたトランザクションの中で実行されます。 暗黙のトランザクションは、コマンドが成功すればコミットされ、コマンドが失敗すればロールバックされます。  
  
## <a name="see-also"></a>参照
 [Cancel 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [CommitTransaction 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [RollbackTransaction 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
