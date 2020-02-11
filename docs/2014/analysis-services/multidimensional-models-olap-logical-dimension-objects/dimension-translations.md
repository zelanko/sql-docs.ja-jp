---
title: ディメンションの翻訳 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81e0ecacaa185b9fe520513af57ced3b382a343c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62728528"
---
# <a name="dimension-translations"></a>ディメンションの翻訳
  翻訳は、ラベルとキャプションの表示言語を変更する単純なメカニズムです。 各翻訳は、値のペアとして定義されます。翻訳済みテキストの文字列と言語 ID の数値とのペアです。 翻訳は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のすべてのオブジェクトで使用できます。 ディメンションは翻訳された属性値も持つことができます。 クライアント アプリケーションは、ユーザーによって定義された言語設定を検索し、すべてのキャプションとラベルの表示をその言語に切り替えます。 1 つのオブジェクトに対する翻訳の数に制限はありません。  
  
 簡単な <xref:Microsoft.AnalysisServices.Translation> オブジェクトは、言語 ID 番号およびキャプションの翻訳で構成されます。 言語 ID 番号は、言語 ID を含む `Integer` です。 キャプションの翻訳は、翻訳されたテキストです。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、ディメンションの翻訳は、ディメンションの名前、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトの名前、またはキャプション、メンバー、階層レベルなどのメンバーの1つの名前を、言語固有で表現したものです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、キューブオブジェクトの翻訳もサポートされています。  
  
 翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。 キューブとキューブのディメンションは、異なる国々のユーザーによって表示されることが頻繁にあります。 キューブやキューブのディメンションのさまざまな要素を異なる言語に翻訳できれば、異なる国々のユーザーがキューブを表示し、理解するのに役立ちます。 たとえば、フランスのビジネス ユーザーは、フランス語ロケールが設定されているワークステーションからキューブにアクセスし、オブジェクト プロパティの値をフランス語で表示できます。 ドイツのビジネス ユーザーがドイツ語ロケールの設定されたワークステーションから同じキューブにアクセスした場合は、オブジェクト プロパティの値をドイツ語で表示できます。  
  
 クライアント コンピューターの照合順序と言語の情報は、ロケール識別子 (LCID) の形式で保存されます。 クライアントは接続時に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに LCID を渡します。 このインスタンスでは LCID を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのメタデータを表示する際にどの翻訳セットを使用するかが決定されます。 指定された翻訳が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトにない場合は、既定言語を使用してコンテンツがクライアントに返されます。  
  
## <a name="see-also"></a>参照  
 [キューブの翻訳](../multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [翻訳 &#40;Analysis Services&#41;](../translations-analysis-services.md)   
 [グローバリゼーションのヒントとベストプラクティス &#40;Analysis Services&#41;](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
