---
title: Statement 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Statement Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Statement
- microsoft.xml.analysis.statement
- urn:schemas-microsoft-com:xml-analysis#Statement
helpviewer_keywords:
- Statement command
ms.assetid: bfedc03c-d476-4d55-b5fd-36169f01351a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96b37de3307a044b046c67bb4ab6fe341ad5e480
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056462"
---
# <a name="statement-element-xmla"></a>Statement 要素 (XMLA)
  `Execute` メソッドを使用して [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに送信されるクエリまたはステートメントを格納します。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Statement` コマンドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに対するクエリまたはステートメントを実行します。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は次の言語をサポートします。  
  
-   多次元式 (MDX) (Multidimensional Expressions (MDX))  
  
-   データ マイニング拡張機能 (MDX)  
  
-   構造化照会言語 (SQL) のサブセット  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
