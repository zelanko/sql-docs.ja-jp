---
title: MDX 構文の要素 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 616cd0bcbf9275598ce94e3935e56e37048f6f64
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033894"
---
# <a name="mdx-syntax-elements-mdx"></a>MDX 構文の要素 (MDX)


  多次元式 (MDX) には、以下に示すような、ほとんどのステートメントで使用される要素、およびほとんどのステートメントに影響を与える要素があります。  
  
|項目|定義|  
|----------|----------------|  
|[識別子](../mdx/identifiers-mdx.md)|識別子は、キューブ、ディメンション、メンバー、およびメジャーなどのオブジェクトの名前です。|  
|**データの種類**|セル、メンバー プロパティ、およびセルのプロパティに含まれるデータの種類を定義します。 MDX は OLE VARIANT データ型だけをサポートします。 VARIANT データ型の強制型変換、変換、および操作の詳細については、プラットフォーム SDK ドキュメントの「VARIANT と VARIANTARG」を参照してください。|  
|[式&#40;MDX&#41;](../mdx/expressions-mdx.md)|式は、Analysis Services を単一の (スカラー) 値またはオブジェクトに解決できる構文の単位です。 式には、単一値、セット式などを返す関数も含まれます。|  
|[演算子](../mdx/operators-mdx-syntax.md)|演算子より複雑な MDX 式を作成する単純なの MDX 式を使用する構文要素を示します。|  
|[関数](../mdx/functions-mdx-syntax.md)|関数とは、0 個以上の入力値を受け入れてスカラー値またはオブジェクトを返す構文要素です。 例としては、[合計](../mdx/sum-mdx.md)いくつかの値を追加するための関数、[メンバー](../mdx/members-set-mdx.md)し、ディメンションまたはレベルからメンバーのセットを返すために機能します。|  
|[コメント](../mdx/comments-mdx-syntax.md)|コメントは、MDX ステートメントまたはステートメントの目的を説明するスクリプトに挿入された文字の部分です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] コメントは実行されません。|  
|[予約済みキーワード](../mdx/reserved-keywords-mdx-syntax.md)|予約済みキーワードは、単語は MDX を使用するために予約されていると、MDX ステートメントで使用するオブジェクト名のない使用する必要があります。|  
|[メンバー、組、およびセット](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)|メンバー、組、およびセットは理解しておく必要がある多次元データの主要な概念、MDX クエリを作成する前にします。|  
  
## <a name="see-also"></a>関連項目  
 [多次元式 &#40;MDX&#41; リファレンス](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
