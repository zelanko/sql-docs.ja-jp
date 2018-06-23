---
title: Alter 要素 (XMLA) |Microsoft ドキュメント
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
- Alter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords:
- Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5ea2c3ed3105c66b0c0848138acb5941978dd9bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083271"
---
# <a name="alter-element-xmla"></a>Alter 要素 (XMLA)
  によって使用される Analysis Services スクリプト言語 (ASSL) 要素が含まれています、 [Execute](../xml-elements-methods-execute.md)メソッドのインスタンス上のオブジェクトを変更する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
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
|子要素|[オブジェクト](../xml-elements-properties/object-element-xmla.md)、 [ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|AllowCreate|省略可能で、`Boolean` 型の属性。`Alter` コマンドで定義されたオブジェクトがまだ存在しない場合、これを作成するかどうかを示します。<br /><br /> true に設定されている場合、`ObjectDefinition` 要素で定義されたオブジェクトが存在しなければ [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上に作成されます。 つまり、オブジェクトがインスタンス上にまだ存在しない場合、`Alter` コマンドは `Create` コマンドのように扱われます。<br /><br /> この属性が省略されている場合、または `false` に設定されている場合には、オブジェクトがまだ存在しなければエラーが発生します。|  
|ObjectExpansion|省略可能で、`Enum` 型の属性。`Execute` メソッドによって実行される変更の程度を定義します。<br /><br /> 場合設定*ObjectProperties*、`ObjectDefinition`要素は、変更対象の主要なオブジェクトの完全な定義のみを含める必要があります下位の副次オブジェクトを含むです。 変更対象のオブジェクトの下位にある主要なオブジェクトは変更されません。 **注:** を使用する場合、 *ObjectProperties*による設定、 [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md)データ型、[データ](../../scripting/objects/data-element-assl.md)関連付けられている要素[ClrAssemblyFile](../../scripting/data-type/clrassemblyfile-data-type-assl.md)データ型が指定する必要はありません。 これが指定されていない場合、`ClrAssembly` は既存のファイルを使用します。 <br /><br /> 場合設定*ExpandFull*、`ObjectDefinition`要素は、変更対象オブジェクトの定義だけでなくも変更するオブジェクトの子孫であるすべての主要なオブジェクトの定義を含める必要があります。 **注:** 、 *ExpandFull*と設定を使用することはできません、[サーバー](../../scripting/objects/server-element-assl.md)要素。|  
|スコープ|省略可能で、`Enum` 型の属性。`ObjectDefinition` 要素内で定義されたオブジェクトの存続期間を定義します。<br /><br /> 場合設定*セッション*で定義されているオブジェクト、`ObjectDefinition`要素は XMLA セッションの存続中にのみ存在します。 **注:** を使用する場合、*セッション*を設定する、`ObjectDefinition`要素を含めることができますのみ[ディメンション](../../scripting/objects/dimension-element-assl.md)、[キューブ](../../scripting/objects/cube-element-assl.md)、または[MiningModel](../../scripting/objects/miningmodel-element-assl.md) ASSL の要素。 <br /><br /> この属性が省略された場合、`ObjectDefinition` 要素内で定義されたオブジェクトは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上に保存されます。|  
  
## <a name="remarks"></a>コメント  
 各`Alter`コマンドで指定された親オブジェクトの下の 1 つの主要なオブジェクトの定義を変更する、 [ParentObject](../xml-elements-properties/parentobject-element-xmla.md)要素。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  