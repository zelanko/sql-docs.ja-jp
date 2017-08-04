---
title: "Wtd (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Wtd function
ms.assetid: 41066e1b-e802-4582-be4b-3ed7807b033e
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1010b6d7aef59c5bb4eb18e93ba63bc972e8b7fa
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="wtd-mdx"></a>Wtd (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  時間ディメンションの週 (Week) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 既定値は型のレベルを持つ最初の階層の現在のメンバーではメンバー式が指定されていない場合は、Time 型の最初のディメンションの週 (**Time.CurrentMember**)、メジャー グループにします。  
  
 **Wtd**関数のショートカット関数では、 [PeriodsToDate](../mdx/periodstodate-mdx.md)レベルに設定されている関数*週間*です。 つまり、`Wtd(Member_Expression)`は等価`PeriodsToDate(Week_Level_Expression,Member_Expression)`です。  
  
## <a name="see-also"></a>参照  
 [Qtd & #40 です。MDX と #41 です。](../mdx/qtd-mdx.md)   
 [Mtd & #40 です。MDX と #41 です。](../mdx/mtd-mdx.md)   
 [Ytd & #40 です。MDX と #41 です。](../mdx/ytd-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

