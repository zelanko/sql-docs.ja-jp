---
title: オブジェクトの定義と識別 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2fd3263a2f8050c36747a81ab3473f5b405ef21
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545030"
---
# <a name="defining-and-identifying-objects-xmla"></a>オブジェクトの定義と識別 (XMLA)
  XML for Analysis (XMLA) コマンド内では、オブジェクト識別子とオブジェクト参照を使用してオブジェクトが識別されます。また、XMLA コマンド内では、Analysis Services Scripting Language (ASSL) 要素を使用してオブジェクトが定義されます。  
  
## <a name="object-identifiers"></a>オブジェクトの識別子  
 オブジェクトは、のインスタンスで定義されているオブジェクトの一意識別子を使用して識別され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 オブジェクト識別子は明示的に指定されるか、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でオブジェクトが作成されるときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって決定されます。 [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)メソッドを使用して、後続の `Discover` または[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッド呼び出しのオブジェクト識別子を取得できます。  
  
## <a name="object-references"></a>オブジェクト参照  
 [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla)や[Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)などのいくつかの XMLA コマンドは、オブジェクト参照を使用して、明確な方法でオブジェクトを参照します。 オブジェクト参照には、コマンドの実行対象となるオブジェクトのオブジェクト識別子と、そのオブジェクトの先祖のオブジェクト識別子が含まれます。 たとえば、パーティションのオブジェクト参照には、パーティションのオブジェクト識別子と、そのパーティションの親メジャー グループ、キューブ、およびデータベースのオブジェクト識別子が含まれます。  
  
## <a name="object-definitions"></a>オブジェクト定義  
 XMLA の[create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)コマンドと[alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)コマンドは、インスタンス上のオブジェクトをそれぞれ作成または変更し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 これらのオブジェクトの定義は、ASSL の要素を含む[Objectdefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)要素によって表されます。 オブジェクト識別子は、 [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)要素を使用して、すべての主要なオブジェクトと多数のマイナーオブジェクトに対して明示的に指定できます。 `ID` 要素が使用されない場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって一意の識別子が提供されます。その際の名前付け規則は識別対象のオブジェクトによって異なります。 コマンドとコマンドを使用してオブジェクトを定義する方法の詳細については `Create` `Alter` 、「 [XMLA&#41;&#40;オブジェクトの作成と変更](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;オブジェクト要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [XMLA&#41;&#40;ParentObject 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [XMLA&#41;&#40;ソース要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [XMLA&#41;&#40;Target 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
