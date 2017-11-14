---
title: "BeginTransaction 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BeginTransaction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 677ad07e9ce6206bbc4e7946ec111f8865bcfcce
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="begintransaction-element-xmla"></a>BeginTransaction 要素 (XMLA)
  インスタンスに現在のセッションでトランザクションを開始[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
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
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **BeginTransaction**コマンドは、現在のセッションにアクティブなトランザクションを開始します。 アクティブなトランザクションが既に存在する場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは現在のセッションのトランザクション参照カウントを増やします。 まだ存在しない場合、インスタンスは新しいトランザクションを開始して、現在のセッションの参照カウントを 1 に設定します。 アクティブなトランザクションを明示的に指定した場合を使用して、 **BeginTransaction**コマンドを明示的に指定されたトランザクション内ですべての後続のコマンドが実行されます。  
  
 現在のセッションが終了したときにトランザクションの参照カウントが 0 より大きければ、すべてのアクティブなトランザクションはロールバックされます。  
  
 明示的に指定されたアクティブなトランザクションが現在のセッションに存在しない場合、現在のセッションで発行されるすべてのコマンドは、暗黙的に定義されたトランザクションの中で実行されます。 暗黙のトランザクションは、コマンドが成功すればコミットされ、コマンドが失敗すればロールバックされます。  
  
## <a name="see-also"></a>参照  
 [要素 &#40; [キャンセル] します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [CommitTransaction 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [RollbackTransaction 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

