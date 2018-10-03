---
title: Create 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Create Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b64f6b222793fdd7c6b92e7462fc10976c0bc139
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051292"
---
# <a name="create-element-xmla"></a>Create 要素 (XMLA)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上にオブジェクトを作成するために `Execute` メソッドによって使用される Analysis Services Scripting Language (ASSL) 要素を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
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
|子要素|[ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md)、 [ParentObject](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|AllowOverwrite|省略可能な`Boolean`属性。 True に設定されている場合、`ObjectDefinition` 要素内で定義されたオブジェクトは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の既存のオブジェクトを上書きできます。 この属性が省略されている場合、または False に設定されている場合は、オブジェクトが既に存在するとエラーが発生します。|  
|スコープ|省略可能な`Enum`属性。 `ObjectDefinition` 要素内で定義されたオブジェクトの存続期間を定義します。 この属性が省略された場合、`ObjectDefinition` 要素内で定義されたオブジェクトは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上に保存されます。 次の値を指定できます。<br /><br /> -   *セッション*<br />     `ObjectDefinition` 要素内で定義されたオブジェクトは、XML for Analysis (XMLA) セッションの期間だけ存続します。 **注:** を使用する場合、*セッション*を設定する、`ObjectDefinition`要素に含めることができますのみ[ディメンション](../../scripting/objects/dimension-element-assl.md)、[キューブ](../../scripting/objects/cube-element-assl.md)、または[MiningModel](../../scripting/objects/miningmodel-element-assl.md) ASSL の要素。|  
  
## <a name="remarks"></a>コメント  
 各 `Create` 操作は、`ParentObject` 要素によって指定される親の下に 1 つの主要なオブジェクトを作成します。 親オブジェクトが省略された場合、作成先の [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスと見なされます。 主要なオブジェクトの親が作成先のインスタンスでない場合には、これによってエラーが発生します。  
  
## <a name="example"></a>例  
 次の例は、`Test Database` という名前の空のデータベースを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上に作成します。  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
