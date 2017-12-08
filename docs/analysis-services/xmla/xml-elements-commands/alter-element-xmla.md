---
title: "Alter 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: Alter Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords: Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 08bc085a99dcd6f9059f1dbba4355aca368bd219
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alter-element-xmla"></a>Alter 要素 (XMLA)
  によって使用される Analysis Services スクリプト言語 (ASSL) 要素が含まれています、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドのインスタンス上のオブジェクトを変更する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
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
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、 [ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|AllowCreate|(省略可能な**ブール**属性) でオブジェクトが定義されているかどうかを示す、 **Alter**まだ存在しない場合、コマンドを作成する必要があります。<br /><br /> 場合に定義されたオブジェクトを true に設定する、 **ObjectDefinition**要素は上に作成、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスの存在しない場合。 言い換えると、 **Alter**コマンドとして扱われます、**作成**コマンドのかどうか、オブジェクトは既にインスタンスに存在しない、します。<br /><br /> この属性を省略した場合またはに設定**false**オブジェクトが存在しない場合にエラーが発生します。|  
|ObjectExpansion|(省略可能な**Enum**属性) によって実行される変更の程度を定義、 **Execute**メソッドです。<br /><br /> 場合設定*ObjectProperties*、 **ObjectDefinition**要素は、変更対象の主要なオブジェクトの完全な定義のみを含める必要があります下位の副次オブジェクトを含むです。 変更対象のオブジェクトの下位にある主要なオブジェクトは変更されません。<br /><br /> 注: を使用する場合、 *ObjectProperties*による設定、 [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)データ型、[データ](../../../analysis-services/scripting/objects/data-element-assl.md)関連付けられている要素[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)データ型が指定する必要はありません。 指定されていない場合、 **ClrAssembly**は既存のファイルを使用します。<br /><br /> 場合設定*ExpandFull*、 **ObjectDefinition**要素は、変更対象オブジェクトの定義だけでなく、オブジェクトの子孫であるすべての主要なオブジェクトの定義を含める必要があります変更します。<br /><br /> 注: *ExpandFull*と設定を使用することはできません、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。|  
|スコープ|(省略可能な**Enum**属性) で定義されているオブジェクトの存続期間を定義、 **ObjectDefinition**要素。<br /><br /> 場合設定*セッション*で定義されているオブジェクト、 **ObjectDefinition**要素は XMLA セッションの存続中にのみ存在します。<br /><br /> 注: を使用する場合、*セッション*を設定する、 **ObjectDefinition**要素を含めることができますのみ[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、または[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL の要素。<br /><br /> この属性を省略するで定義されたオブジェクト、 **ObjectDefinition**要素が上に保持されます、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。|  
  
## <a name="remarks"></a>解説  
 各**Alter**コマンドで指定された親オブジェクトの下の 1 つの主要なオブジェクトの定義を変更する、 [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)要素。  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
