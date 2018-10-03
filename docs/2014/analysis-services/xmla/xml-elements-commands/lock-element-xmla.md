---
title: 要素 (XMLA) のロック |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Lock Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aee5d603c2708cb42b666d3cc0c9acc5ea208f0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079522"
---
# <a name="lock-element-xmla"></a>Lock 要素 (XMLA)
  上の指定したオブジェクトをロック、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
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
|子要素|[ID](../xml-elements-properties/id-element-xmla.md)、[モード](../xml-elements-properties/mode-element-xmla.md)、[オブジェクト](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Lock` コマンドは、現在アクティブなトランザクションのコンテキスト内で、共有オブジェクトまたは排他的に使用されるオブジェクトをロックします。 `Lock` コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけです。 オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、共有ロックと排他ロックの 2 種類がサポートされています。 サポートされているロックの種類の詳細については[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[Mode 要素&#40;XMLA&#41;](../xml-elements-properties/mode-element-xmla.md)します。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、データベースに対するロックだけが可能です。 `Object` 要素には、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースへのオブジェクト参照を含める必要があります。 `Object` 要素が指定されていない場合、またはデータベース以外のオブジェクトを `Object` 要素が参照している場合には、エラーが発生します。  
  
 他のコマンドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースに対する `Lock` コマンドを暗黙的に発行します。 データベースからデータまたはメタデータを読み取るすべての操作 (たとえば `Discover` メソッドや、`Execute` コマンドを実行する `Statement` メソッド) は、データベースに対する共有ロックを暗黙的に発行します。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース上のオブジェクトに対してデータまたはメタデータの変更内容をコミットするすべてのトランザクション (たとえば `Execute` コマンドを実行する `Alter` メソッド) は、データベースに対する排他ロックを暗黙的に発行します。  
  
 すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。 現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。  
  
## <a name="see-also"></a>参照  
 [要素のロック解除&#40;XMLA&#41;](lock-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
