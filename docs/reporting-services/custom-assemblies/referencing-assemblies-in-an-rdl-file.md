---
title: "RDL ファイル内のアセンブリを参照している |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 87609ab5b118eaa696f7152b25cf7e984e7f6e7f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="referencing-assemblies-in-an-rdl-file"></a>RDL ファイルのアセンブリの参照
  RDL 仕様にレポート定義ファイルでカスタム コード アセンブリの使用をサポートするために 2 つのレポート定義言語 (RDL) 要素が含まれている: **CodeModules**要素および**クラス**要素。  
  
 **CodeModules**要素では、レポート式でマネージ コード アセンブリを参照することができます。 **CodeModules**特殊な関数を呼び出すことで、レポート定義ファイルを使用するアセンブリへの参照を含む最上位の要素。 カスタム アセンブリの使用をサポートするレポート定義のエントリは次のようになります。  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 呼び出す代わりに<xref:System.Reflection.Assembly.Load%2A>、カスタム コードから手動で追加するかによって、カスタム アセンブリを登録**CodeModule**要素を RDL ファイルにまたはを使用して、**参照**のタブ、**レポート プロパティ**ダイアログ。 詳細については、「 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)を表しています。  
  
 **クラス**要素が、レポート定義のインスタンス メンバーの使用をサポートします。 **クラス**クラス名とインスタンス名への参照を含む最上位の要素。 インスタンス メンバーの使用をサポートするレポート定義のエントリは次のようになります。  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 詳細については、次を参照してください。 [Custom Assemblies Through Expressions にアクセスする](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md)です。  
  
## <a name="see-also"></a>参照  
 [レポートでカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
