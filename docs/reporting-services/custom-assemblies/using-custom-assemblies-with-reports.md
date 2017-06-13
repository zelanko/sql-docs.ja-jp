---
title: "レポートでカスタム アセンブリの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: fb818ce570a542a3cfcccec5c9290821c4e21181
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="using-custom-assemblies-with-reports"></a>レポートでのカスタム アセンブリの使用
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート アイテムの値、スタイル、および書式設定に関するカスタム コードを記述できます。 たとえば、カスタム コードを使用して、ロケールに基づいて通貨を書式設定したり、特殊な書式設定の特定の値にフラグを設定したり、または企業で実際に使用している他のビジネス ルールを適用したりすることができます。 使用してカスタム コード アセンブリを作成するには、レポートにこのコードを追加する方法、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]レポート定義ファイル内から参照できるようにします。 サーバーは、レポートを実行するときにカスタム アセンブリの関数を呼び出します。 カスタム アセンブリは、レポートで使用する特別な関数を取得するときに使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [RDL ファイル内のアセンブリを参照します。](../../reporting-services/custom-assemblies/referencing-assemblies-in-an-rdl-file.md)  
 レポート定義言語ファイルのカスタム アセンブリを参照する方法について説明します。  
  
 [カスタム アセンブリの配置](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md)  
 カスタム アセンブリをレポート デザイナーとレポート サーバーに配置する方法について説明します。  
  
 [カスタム アセンブリの厳密な名前を使用します。](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md)  
 複雑な名前を持つカスタム アセンブリの使用方法について説明します。  
  
 [カスタム アセンブリのアクセス許可のアサート](../../reporting-services/custom-assemblies/asserting-permissions-in-custom-assemblies.md)  
 カスタム アセンブリの権限を限定して配置する方法と権限をコード内でアサートする方法について説明します。  
  
 [式を介してカスタム アセンブリへのアクセス](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md)  
 カスタム アセンブリ メソッドをレポート定義のレポート式として呼び出す方法について説明します。  
  
 [カスタム アセンブリ オブジェクトの初期化](../../reporting-services/custom-assemblies/initializing-custom-assembly-objects.md)  
 レポートから呼び出されたカスタム アセンブリ オブジェクトの値を初期化する方法について説明します。  
  
 [方法: カスタム アセンブリのデバッグ](../../reporting-services/custom-assemblies/how-to-debug-custom-assemblies.md)  
 カスタム アセンブリ コードのデバッグ方法について説明します。  
  
## <a name="see-also"></a>参照  
 [レポート定義言語 & #40 です。SSRS &#41;](../../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
