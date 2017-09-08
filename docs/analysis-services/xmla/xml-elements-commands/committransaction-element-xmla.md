---
title: "CommitTransaction 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CommitTransaction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CommitTransaction
- urn:schemas-microsoft-com:xml-analysis#CommitTransaction
- microsoft.xml.analysis.committransaction
helpviewer_keywords:
- CommitTransaction command
ms.assetid: 1cd814dc-a0be-4305-b44d-faf15e843f7d
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94e3d90ec0e59226045fc12e460768abbb6ae78a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="committransaction-element-xmla"></a>CommitTransaction 要素 (XMLA)
  現在のセッションでトランザクションをコミットする[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <CommitTransaction />  
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
 **CommitTransaction**コマンドが明示的に定義を使用して、アクティブなトランザクションをコミット、 **BeginTransaction**現在のセッションでの要素。 既存のアクティブなトランザクションがない場合、エラーが発生します。 アクティブなトランザクションが既に存在する場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは現在のセッションのトランザクション参照カウントを減らします。 明示的に定義されたアクティブなトランザクションの参照カウントが 0 に達した場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスはトランザクションをコミットします。  
  
## <a name="see-also"></a>参照  
 [BeginTransaction 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [要素 &#40; [キャンセル] します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [RollbackTransaction 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
