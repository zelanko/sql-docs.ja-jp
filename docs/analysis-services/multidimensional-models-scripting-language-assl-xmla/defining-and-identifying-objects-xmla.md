---
title: "定義するオブジェクトと識別 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d2d39b5057dd00d310c1d4f5581228ed6ae27ea0
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="defining-and-identifying-objects-xmla"></a>オブジェクトの定義と識別 (XMLA)
  XML for Analysis (XMLA) コマンド内では、オブジェクト識別子とオブジェクト参照を使用してオブジェクトが識別されます。また、XMLA コマンド内では、Analysis Services Scripting Language (ASSL) 要素を使用してオブジェクトが定義されます。  
  
## <a name="object-identifiers"></a>オブジェクト識別子  
 インスタンスに定義されているオブジェクトの一意識別子を使用して、オブジェクトが識別される[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 オブジェクト識別子は明示的に指定されるか、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でオブジェクトが作成されるときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって決定されます。 使用することができます、 [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)のオブジェクト識別子を取得する方法を後続**Discover**または[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
## <a name="object-references"></a>オブジェクトの参照  
 いくつかの XMLA コマンドなど[削除](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)または[プロセス](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)、明確な方法でオブジェクトを参照するオブジェクト参照を使用します。 オブジェクト参照には、コマンドの実行対象となるオブジェクトのオブジェクト識別子と、そのオブジェクトの先祖のオブジェクト識別子が含まれます。 たとえば、パーティションのオブジェクト参照には、パーティションのオブジェクト識別子と、そのパーティションの親メジャー グループ、キューブ、およびデータベースのオブジェクト識別子が含まれます。  
  
## <a name="object-definitions"></a>オブジェクト定義  
 [作成](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)と[Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) XMLA のコマンドを作成または変更、それぞれ、オブジェクトで、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。 これらのオブジェクトの定義がによって表される、 [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) ASSL の要素を含む要素です。 オブジェクト識別子を明示的に指定するすべての主要なと多くの副次オブジェクトを使用して、 [ID](../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)要素。 場合、 **ID**要素は使用されず、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスを特定するオブジェクトに依存する名前付け規則に、一意の識別子を提供します。 使用する方法についての詳細、**作成**と**Alter** 、オブジェクトを定義するためのコマンドを参照してください[作成し、オブジェクトの変更 &#40;です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>参照  
 [Object 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [ParentObject 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Source 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [ターゲット要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
