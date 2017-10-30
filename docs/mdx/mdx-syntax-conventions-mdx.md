---
title: "MDX 構文表記規則 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], syntax
- MDX [Analysis Services], syntax
ms.assetid: 50a6e723-91c4-407b-a0d5-87d0d4e4e0f6
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 522b9ad28f712c52e603a2eaf539bb76f4dd0bd6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-syntax-conventions-mdx"></a>MDX 構文の表記規則 (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  MDX 言語リファレンスにある多次元式 (MDX) の構文図では、以下の表記規則を使用しています。  
  
|表記|使用方法|  
|----------------|-----------|  
|*斜体*|ユーザーが指定する MDX 構文の引数を示します。|  
|(& a) #124 です。(縦棒)|角かっこまたは中かっこで囲まれた構文項目を区切ります。 項目の 1 つだけを選択することができます。|  
|`[ ]`(かっこ)|省略可能な構文項目を示します。 角かっこは入力しません。|  
|[,] ...n|先行する項目を、任意の回数繰り返せることを示します。 項目はコンマで区切ることもあります。|  
|\<ラベル >:: =|構文のブロックの名前を示します。 この表記は、1 つのステートメント内の複数の箇所で使用できる長い構文の一部または構文の 1 単位をグループにまとめて、ラベルを付けるために使用します。 構文のブロックを使用できる箇所は山かっこで囲まれたラベル:\<ラベル >。|  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-language-reference-mdx.md)  
  
  


