---
title: MDX による多次元データを照会 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe45a4f8fab7066ff3f606210774463f14559af7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021695"
---
# <a name="querying-multidimensional-data-with-mdx"></a>MDX による多次元データのクエリ
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多次元式 (MDX) は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で多次元データを操作および取得する際に使用するクエリ言語です。 MDX は XML for Analysis (XMLA) 仕様をベースとして、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]用の拡張機能を加えたものです。 MDX の式は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が評価することでセットやメンバーなどのオブジェクトを取得できる識別子、値、ステートメント、関数、および演算子の組み合わせです。また、文字列や数値などのスカラー値も使用されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の MDX クエリおよび MDX 式は、次の操作を実行するために使用されます。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] キューブからクライアント アプリケーションにデータを返す。  
  
-   クエリ結果の書式を設定する。  
  
-   計算されるメンバー、名前付きセット、スコープ割り当て、および主要業績評価指標 (KPI) の定義など、キューブのデザイン タスクを実行する。  
  
-   ディメンションおよびセルのセキュリティなど、管理タスクを実行する。  
  
 MDX は、一見、多くの点で、リレーショナル データベースで通常使用される SQL 構文に似ています。 ただし、MDX は、SQL 言語を拡張したものではなく、SQL とは多くの点で異なります。 キューブをデザインしたりセキュリティで保護する際に使用する MDX 式の作成、または多次元データを返して書式を設定する MDX クエリの作成を行うには、MDX の基本的な概念と、ディメンション モデリング、MDX 構文要素、MDX 演算子、MDX ステートメント、および MDX 関数を理解しておく必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[MDX & #40; の主な概念Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)|多次元式 (MDX) を使用すると、多次元データに対するクエリの実行や、キューブ内で使用する MDX 式の作成を行うことができますが、まず [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のディメンションの概念と用語を理解しておく必要があります。|  
|[MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)|多次元式 (MDX) を使用すると、多次元オブジェクト (キューブなど) に対してクエリを実行し、キューブ データが格納された多次元セル セットを返すことができます。 このトピックとサブトピックでは、MDX クエリの概要を説明します。|  
|[MDX スクリプティングの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の多次元式 (MDX) スクリプトは、計算結果をキューブに格納する 1 つまたは複数の MDX 式またはステートメントから構成されます。<br /><br /> MDX スクリプトはキューブの計算プロセスを定義します。 また、MDX スクリプト自体がキューブの一部分だと考えることもできます。 したがって、キューブに関連した MDX スクリプトの内容を変更すると、即座にキューブの計算プロセスが変更されることになります。<br /><br /> MDX スクリプトを生成するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でキューブ デザイナーを使用できます。|  
  
## <a name="see-also"></a>参照  
 [MDX 構文の要素 & #40 です。MDX と #41 です。](../../../mdx/mdx-syntax-elements-mdx.md)   
 [MDX 言語リファレンス & #40 です。MDX と #41 です。](../../../mdx/mdx-language-reference-mdx.md)  
  
  
