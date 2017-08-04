---
title: "組関数の使用 |Microsoft ドキュメント"
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
- tuple functions
ms.assetid: fe41e3e5-a675-4169-a966-b42c18e8d741
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b92f048f50f26d6ba5c98e28193a44a68e3ceb39
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="using-tuple-functions"></a>組関数の使用
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  組関数は、組をセットから取得します。または、組の文字列表記を解決することによって組を取得します。  
  
 組関数は、メンバー関数や集合関数と同様に、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用される多次元構造を操作するために不可欠です。  
  
 MDX では、次の 3 つの組関数がある[現在 & #40 です。MDX と #41 です。](../mdx/current-mdx.md)、[項目 & #40 です。組と #41 です。& #40 です。MDX と #41 です。](../mdx/item-tuple-mdx.md)と[StrToTuple (& a) #40 です。MDX と #41 です。](../mdx/strtotuple-mdx.md). 次のクエリの例では、各組関数の使用方法を示します。  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [関数と #40 です。MDX 構文 &#41;](../mdx/functions-mdx-syntax.md)   
 [メンバー関数の使用](../mdx/using-member-functions.md)   
 [集合関数の使用](../mdx/using-set-functions.md)  
  
  

