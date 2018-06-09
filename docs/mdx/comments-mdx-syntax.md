---
title: コメント (MDX 構文) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 17693d0dc76dd6cb8b3a4d0c3ead9f95c0599580
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740763"
---
# <a name="comments-mdx-syntax"></a>コメント (MDX 構文)


  コメントは、プログラム コード内の実行されないテキスト文字列です  (コメントは "注釈" とも呼ばれます)。 コメントは、コードについて説明したり、診断中の多次元式 (MDX) ステートメントやスクリプトの特定部分を一時的に無効にしたりするために使用します。 コードを説明するコメントを使用すると、することができます後でプログラム コードの保守容易にします。 また、プログラム名、作成者名、およびコードの主要な変更日を記録するためにコメントを使用する場合も少なくありません。 コメントは、複雑な計算の解説やプログラミング方法の説明にも使用できます。  
  
 MDX のコメントは、以下のガイドラインに従います。  
  
-   コメント内ではすべてのアルファベット文字と記号を使用できます。  コメント内のすべての文字は無視されます。  
  
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
  
  
