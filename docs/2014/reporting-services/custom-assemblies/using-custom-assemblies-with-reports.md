---
title: レポートでのカスタム アセンブリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e79f48f4e4a2eb5fbc83c353461709658caf2509
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63265662"
---
# <a name="using-custom-assemblies-with-reports"></a>レポートでのカスタム アセンブリの使用
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート アイテムの値、スタイル、および書式設定に関するカスタム コードを記述できます。 たとえば、カスタム コードを使用して、ロケールに基づいて通貨を書式設定したり、特殊な書式設定の特定の値にフラグを設定したり、または企業で実際に使用している他のビジネス ルールを適用したりすることができます。 このコードをレポートに含める方法の1つは、レポート定義ファイル内から参照[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]できるを使用して、カスタムコードアセンブリを作成することです。 サーバーは、レポートを実行するときにカスタム アセンブリの関数を呼び出します。 カスタム アセンブリは、レポートで使用する特別な関数を取得するときに使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [RDL ファイルのアセンブリの参照](referencing-assemblies-in-an-rdl-file.md)  
 レポート定義言語ファイルのカスタム アセンブリを参照する方法について説明します。  
  
 [カスタム アセンブリの配置](deploying-a-custom-assembly.md)  
 カスタム アセンブリをレポート デザイナーとレポート サーバーに配置する方法について説明します。  
  
 [複雑な名前を持つカスタム アセンブリの使用](using-strong-named-custom-assemblies.md)  
 複雑な名前を持つカスタム アセンブリの使用方法について説明します。  
  
 [カスタム アセンブリでの権限のアサート](asserting-permissions-in-custom-assemblies.md)  
 カスタム アセンブリの権限を限定して配置する方法と権限をコード内でアサートする方法について説明します。  
  
 [式を使用したカスタム アセンブリへのアクセス](accessing-custom-assemblies-through-expressions.md)  
 カスタム アセンブリ メソッドをレポート定義のレポート式として呼び出す方法について説明します。  
  
 [カスタム アセンブリ オブジェクトの初期化](initializing-custom-assembly-objects.md)  
 レポートから呼び出されたカスタム アセンブリ オブジェクトの値を初期化する方法について説明します。  
  
 [カスタム アセンブリをデバッグする方法](how-to-debug-custom-assemblies.md)  
 カスタム アセンブリ コードのデバッグ方法について説明します。  
  
## <a name="see-also"></a>参照  
 [レポート定義言語 &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md)  
  
  
