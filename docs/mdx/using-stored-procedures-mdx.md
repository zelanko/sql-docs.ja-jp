---
title: "ストアド プロシージャ (MDX) を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- user-defined functions [MDX]
- stored procedures [MDX]
ms.assetid: 818fb2ad-f88b-4d0c-9f70-f378aed42e8e
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 187b71551aa1001a777486da08f3f10e171f2302
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-stored-procedures-mdx"></a>ストアド プロシージャの使用 (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  .NET ストアド プロシージャやユーザー定義関数を記述して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] および多次元式 (MDX) の機能を拡張できます。 詳細については、次を参照してください[ADOMD.NET サーバー プログラミング。](../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
 ストアド プロシージャを参照する、または呼び出す場合、名前の後にかっこを付けて関数名を指定します。 かっこ内には、引数、つまりパラメーターに設定するデータを指定する式を指定することができます。 関数を呼び出す場合、すべてのパラメーターに対する引数値を指定する必要があります。また、引数値を指定する順序は、ユーザー定義関数でパラメーターの定義された順序と同一である必要があります。  
  
 次のクエリでは、SampleAssembly という名前のアセンブリが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーに登録されていることを前提としています。  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *ストアド プロシージャ*で使用される用語は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のこれらの種類の関数。 以前のバージョンの[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]関数としてのこれらの型と呼ばれる*ユーザー定義関数*です。  
  
## <a name="types-of-stored-procedures"></a>ストアド プロシージャの種類  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は COM アセンブリと CLR アセンブリの両方をサポートします。 CLR アセンブリでは使用可能なセキュリティが拡張されているため、CLR アセンブリをお勧めします。 サーバーに Microsoft Office Excel がインストールされている場合、Excel 関数も使用可能です。  
  
> [!NOTE]  
>  Microsoft Visual Basic for Applications (VBA) COM アセンブリは自動的に登録されます。  
  
## <a name="see-also"></a>参照  
 [関数と #40 です。MDX 構文 &#41;](../mdx/functions-mdx-syntax.md)  
  
  
