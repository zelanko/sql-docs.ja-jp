---
title: キューブの翻訳 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82ded06c9008e4a403e5707a4a0b2fafec261e58
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="cube-translations"></a>キューブの翻訳
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  翻訳は、ラベルとキャプションの表示言語を変更する単純なメカニズムです。 各翻訳は、値のペアとして定義されます。翻訳済みテキストの文字列と言語 ID の数値とのペアです。 翻訳は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のすべてのオブジェクトで使用できます。 ディメンションは翻訳された属性値も持つことができます。 クライアント アプリケーションは、ユーザーによって定義された言語設定を検索し、すべてのキャプションとラベルの表示をその言語に切り替えます。 1 つのオブジェクトに対する翻訳の数に制限はありません。  
  
 簡単な <xref:Microsoft.AnalysisServices.Translation> オブジェクトは、言語 ID 番号およびキャプションの翻訳で構成されます。 言語 ID 番号は、**整数**言語 ID に置き換えます。 キャプションの翻訳は、翻訳されたテキストです。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]キューブの翻訳は、キャプションや表示フォルダーなど、キューブ オブジェクトの名前の言語に固有の表現。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  では、ディメンション名およびメンバー名の翻訳もサポートされています。  
  
 翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。 同じキューブ データが、異なる国々のユーザーによって表示されることがよくあります。 キューブのさまざまな要素を異なる言語に翻訳できれば、異なる国々のユーザーがキューブのメタデータを表示し、理解するのに役立ちます。 たとえば、フランスのビジネス ユーザーは、フランス語のロケール設定のワークステーションからキューブにアクセスし、オブジェクト プロパティの値をフランス語で表示できます。 同様に、ドイツのビジネス ユーザーがドイツ語のロケール設定のワークステーションから同じキューブにアクセスすると、オブジェクト プロパティの値をドイツ語で表示できます。  
  
 クライアント コンピューターの照合順序と言語の情報は、ロケール識別子 (LCID) の形式で保存されます。 クライアントは接続時に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに LCID を渡します。 このインスタンスでは LCID を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのメタデータを各ビジネス ユーザーに表示する際にどの翻訳セットを使用するかが決定されます。 指定された翻訳が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトにない場合は、既定言語を使用してコンテンツがクライアントに返されます。  
  
## <a name="see-also"></a>参照  
 [ディメンションの翻訳](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Analysis Services での翻訳のサポート](../../analysis-services/translation-support-in-analysis-services.md)   
 [グローバリゼーションのヒントとベスト プラクティス (&) #40 です。Analysis Services & #41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
