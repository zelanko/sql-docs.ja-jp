---
title: ストアド プロシージャ (MDX) を使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- user-defined functions [MDX]
- stored procedures [MDX]
ms.assetid: 818fb2ad-f88b-4d0c-9f70-f378aed42e8e
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: fff3b831a076ad4c6d2dfb5f2cdeb134bd3341cb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-stored-procedures-mdx"></a>ストアド プロシージャの使用 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [関数&#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)  
  
  
