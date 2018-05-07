---
title: コメント (MDX 構文) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- remarks [MDX]
- MDX [Analysis Services], comments
- commenting characters
- nonexecuting text strings [MDX]
- Multidimensional Expressions [Analysis Services], comments
- comments [MDX]
ms.assetid: 9c00b30c-28f6-4f23-b812-ccc0e900daa5
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5fedab997ad555c49342a0aea60575b30a74dcd9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="comments-mdx-syntax"></a>コメント (MDX 構文)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  コメントは、プログラム コード内の実行されないテキスト文字列です  (コメントは "注釈" とも呼ばれます)。 コメントは、コードについて説明したり、診断中の多次元式 (MDX) ステートメントやスクリプトの特定部分を一時的に無効にしたりするために使用します。 コードを説明するコメントを使用すると、することができます後でプログラム コードの保守容易にします。 また、プログラム名、作成者名、およびコードの主要な変更日を記録するためにコメントを使用する場合も少なくありません。 コメントは、複雑な計算の解説やプログラミング方法の説明にも使用できます。  
  
 MDX のコメントは、以下のガイドラインに従います。  
  
-   コメント内ではすべてのアルファベット文字と記号を使用できます。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] コメント内のすべての文字を無視します。  
  
-   ステートメント内またはスクリプト内のコメント長には制限がありません。 1 行または複数行のコメントを作成できます。  
  
 MDX では、次の 3 種類のコメント文字がサポートされます。  
  
 // (二重スラッシュ)  
 このコメント文字では、実行コードと同じ行にコメントを記述できます。コメント専用の行にすることもできます。 2 重スラッシュの後ろから行末までがコメント部分です。 複数行にわたってコメントを記述する場合、それぞれのコメント行の先頭に二重スラッシュを入力する必要があります。 詳細については、次を参照してください。 [&#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)です。  
  
 -- (二重ハイフン)  
 このコメント文字では、実行コードと同じ行にコメントを記述できます。コメント専用の行にすることもできます。 二重ハイフンの後ろから行末までがコメント部分です。 複数行にわたってコメントを記述する場合、それぞれのコメント行の先頭に二重ハイフンを入力する必要があります。 詳細については、次を参照してください。 [--&#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)です。  
  
 /* ...\*/(スラッシュとアスタリスク文字のペア)  
 このコメント文字では、実行コードと同じ行にコメントを記述できるほか、コメント専用の行にすることもできます。さらに、実行可能コード内でもこのコメント文字を使用できます。 コメント開始記号からのすべてのもの (/\*) にコメント終了記号 (\*/)、コメントの一部と見なされます。 複数行のコメントでは、コメント文字のペアの (/\*)、コメント、および閉じるコメント文字のペアを開始する必要があります (\*/)、コメントを終了する必要があります。 コメント行ではそれ以外のコメント文字を使用できません。 詳細については、次を参照してください[/*.。\*/ (Comment)](../mdx/comment-mdx.md).  
  
## <a name="example"></a>例  
 次のクエリでは、3 種類すべてのコメントの例を示します。  
  
 `//An example of a comment using the double-forward slash`  
  
 `--An example of a comment using the double-hypen`  
  
 `/*An example of a`  
  
 `multi-line`  
  
 `comment*/`  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 構文の要素&#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
