---
title: MDX クエリの基礎 (Analysis Services) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b4d1309a411688e79f9f44e58dba65add8434611
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-query-fundamentals-analysis-services"></a>MDX クエリの基礎 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多次元式 (MDX) を使用すれば、多次元オブジェクト (たとえばキューブ) をクエリして、キューブ データが格納された多次元セル セットを返すことができます。 このトピックとサブトピックでは、MDX クエリの概要を説明します。  
  
 以下のトピックでは、MDX クエリとクエリが作成するセル セットについて、および基本的な MDX 構文の詳細について説明します。  
  
> [!NOTE]  
>  MDX クエリおよび計算に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=81621)」の「効率的な MDX の記述」セクションを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[MDX の基本的なクエリ & #40 です。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)|MDX SELECT ステートメントの基本的な構文について説明します。|  
|[クエリおよびスライサー軸とクエリを制限する&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-restricting-the-query.md)|クエリ軸とスライサー軸、およびそれらを指定する方法について説明します。|  
|[クエリ & #40; 内のキューブ コンテキストの確立MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)|MDX SELECT ステートメントでの FROM 句の用途を説明します。|  
|[MDX & #40; 内のセットを名前付きの作成MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)|MDX での名前付きセットの用途と、名前付きセットを MDX クエリ内で作成および使用するために必要なテクニックについて説明します。|  
|[計算されるメンバーを MDX に & #40; の作成MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md)|MDX での計算されるメンバーに関する情報と、計算されるメンバーを MDX 式内で作成および使用するために必要なテクニックについて説明します。|  
|[MDX & #40; でのセル計算の作成MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)|計算されるセルを作成および使用する処理の詳細について説明します。|  
|[作成とプロパティの値 & #40; を使用MDX と #41 です。](http://msdn.microsoft.com/library/0cafb269-03c8-4183-b6e9-220f071e4ef2)|ディメンション、レベル、メンバー、およびセルの各プロパティの作成時および使用時の処理の詳細について説明します。|  
|[操作に使用するデータ & #40 です。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)|ドリルスルーとロールアップを使ったデータ操作の基礎について、および MDX でのパス順序と解決順序について説明します。|  
|[データ & #40; を変更します。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-modifying-data.md)|書き戻しを使って多次元データを一時的または永続的に変更する方法について説明します。|  
|[変数とパラメーター & #40; を使用します。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|MDX クエリ内での変数およびパラメーターの使用方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元式 & #40 です。MDX と #41 です。参照](../../../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
