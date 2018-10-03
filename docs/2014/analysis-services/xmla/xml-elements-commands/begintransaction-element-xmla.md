---
title: BeginTransaction 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- BeginTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5e8b1954836a7c5b079d629602d03ba4b45d8620
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083472"
---
# <a name="begintransaction-element-xmla"></a>BeginTransaction 要素 (XMLA)
  インスタンスと現在のセッションでトランザクションを開始[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `BeginTransaction` コマンドは、アクティブなトランザクションを現在のセッションで開始します。 アクティブなトランザクションが既に存在する場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは現在のセッションのトランザクション参照カウントを増やします。 まだ存在しない場合、インスタンスは新しいトランザクションを開始して、現在のセッションの参照カウントを 1 に設定します。 アクティブなトランザクションが `BeginTransaction` コマンドを使用して明示的に指定された場合、後続のすべてのコマンドは、明示的に指定されたトランザクション内で実行されます。  
  
 現在のセッションが終了したときにトランザクションの参照カウントが 0 より大きければ、すべてのアクティブなトランザクションはロールバックされます。  
  
 明示的に指定されたアクティブなトランザクションが現在のセッションに存在しない場合、現在のセッションで発行されるすべてのコマンドは、暗黙的に定義されたトランザクションの中で実行されます。 暗黙のトランザクションは、コマンドが成功すればコミットされ、コマンドが失敗すればロールバックされます。  
  
## <a name="see-also"></a>参照  
 [Cancel 要素&#40;XMLA&#41;](cancel-element-xmla.md)   
 [CommitTransaction 要素&#40;XMLA&#41;](committransaction-element-xmla.md)   
 [RollbackTransaction 要素&#40;XMLA&#41;](rollbacktransaction-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
