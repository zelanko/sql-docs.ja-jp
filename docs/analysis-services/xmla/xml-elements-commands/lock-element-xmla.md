---
title: "ロック要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Lock Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords: Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 98e5087dc10ae495dec711c35fa807cb9fd68e02
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="lock-element-xmla"></a>Lock 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]上の指定したオブジェクトをロック、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)、[モード](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md)、[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **ロック**コマンドが現在アクティブなトランザクションのコンテキスト内で、共有、または排他的に使用のいずれかのオブジェクトをロックします。 データベース管理者またはサーバー管理者のみに明示的に発行できる、**ロック**コマンド。 オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、共有ロックと排他ロックの 2 種類がサポートされています。 サポートされているロックの種類の詳細については[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[Mode 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、データベースに対するロックだけが可能です。 **オブジェクト**要素へのオブジェクト参照を含める必要があります、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 場合、**オブジェクト**要素が指定されていない場合は、**オブジェクト**要素を参照し、データベース以外のオブジェクト、エラーが発生します。  
  
 他のコマンドの問題では暗黙的に、**ロック**コマンドを[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 いずれかなど、データベースからデータまたはメタデータを読み取る操作**Discover**メソッドまたは**Execute**実行されているメソッド、**ステートメント**コマンドで、共有を暗黙的に発行データベースに対してロックします。 オブジェクトへのデータまたはメタデータの変更をコミットするすべてのトランザクション、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]などのデータベース、 **Execute**実行されているメソッド、 **Alter**コマンドでの排他ロックを暗黙的に発行しますデータベースです。  
  
 すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。 現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。  
  
## <a name="see-also"></a>参照  
 [要素 &#40; をロック解除します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
