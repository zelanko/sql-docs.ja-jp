---
title: ディメンションの翻訳 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b58303abfd94710452143e014fee0019826a2a97
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68180765"
---
# <a name="dimension-translations"></a>ディメンションの翻訳
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  翻訳は、ラベルとキャプションの表示言語を変更する単純なメカニズムです。 各翻訳は、値のペアとして定義されます。翻訳済みテキストの文字列と言語 ID の数値とのペアです。 翻訳は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のすべてのオブジェクトで使用できます。 ディメンションは翻訳された属性値も持つことができます。 クライアント アプリケーションは、ユーザーによって定義された言語設定を検索し、すべてのキャプションとラベルの表示をその言語に切り替えます。 1 つのオブジェクトに対する翻訳の数に制限はありません。  
  
 簡単な <xref:Microsoft.AnalysisServices.Translation> オブジェクトは、言語 ID 番号およびキャプションの翻訳で構成されます。 言語 ID 番号は、**整数**言語 ID に置き換えます。 キャプションの翻訳は、翻訳されたテキストです。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、ディメンションの翻訳は、ディメンションの名前の名の言語固有の表現、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトまたはキャプション、メンバー、または階層のレベルなど、そのメンバーの 1 つ。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] また、キューブ オブジェクトの翻訳もサポートしています。  
  
 翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。 キューブとキューブのディメンションは、異なる国々のユーザーによって表示されることが頻繁にあります。 キューブやキューブのディメンションのさまざまな要素を異なる言語に翻訳できれば、異なる国々のユーザーがキューブを表示し、理解するのに役立ちます。 たとえば、フランスのビジネス ユーザーは、フランス語ロケールが設定されているワークステーションからキューブにアクセスし、オブジェクト プロパティの値をフランス語で表示できます。 ドイツのビジネス ユーザーがドイツ語ロケールの設定されたワークステーションから同じキューブにアクセスした場合は、オブジェクト プロパティの値をドイツ語で表示できます。  
  
 クライアント コンピューターの照合順序と言語の情報は、ロケール識別子 (LCID) の形式で保存されます。 クライアントは接続時に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに LCID を渡します。 このインスタンスでは LCID を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのメタデータを表示する際にどの翻訳セットを使用するかが決定されます。 指定された翻訳が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトにない場合は、既定言語を使用してコンテンツがクライアントに返されます。  
  
## <a name="see-also"></a>関連項目  
 [キューブの翻訳](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Analysis Services での翻訳のサポート](../../analysis-services/translation-support-in-analysis-services.md)   
 [グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
