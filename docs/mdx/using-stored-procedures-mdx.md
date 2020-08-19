---
description: ストアド プロシージャの使用 (MDX)
title: ストアドプロシージャの使用 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2c9bd8f20ffae61656dd30f139ce12665ff57f4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476974"
---
# <a name="using-stored-procedures-mdx"></a>ストアド プロシージャの使用 (MDX)


  .NET ストアド プロシージャやユーザー定義関数を記述して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] および多次元式 (MDX) の機能を拡張できます。 詳細については、「 [ADOMD.NET Server プログラミング](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)」を参照してください。  
  
 ストアドプロシージャを参照したり呼び出したりする場合は、関数名の後にかっこを指定します。 かっこ内で、パラメーターに渡されるデータを提供する引数と呼ばれる式を指定できます。 関数を呼び出す場合は、すべてのパラメーターに引数の値を指定する必要があります。また、パラメーターがユーザー定義関数で定義されているのと同じ順序で引数値を指定する必要があります。  
  
 次のクエリでは、SampleAssembly という名前のアセンブリが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーに登録されていることを前提としています。  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *ストアドプロシージャ* は、これらの種類の関数で使用される用語です [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。 以前のバージョンのでは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、これらの型の関数を *ユーザー定義関数*と呼びました。  
  
## <a name="types-of-stored-procedures"></a>ストアドプロシージャの種類  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は COM アセンブリと CLR アセンブリの両方をサポートします。 Clr アセンブリで使用可能なセキュリティが強化されているため、CLR アセンブリを使用することをお勧めします。 サーバーに Microsoft Office Excel がインストールされている場合、Excel 関数も使用可能です。  
  
> [!NOTE]  
>  Microsoft Visual Basic for Applications (VBA) COM アセンブリは自動的に登録されます。  
  
## <a name="see-also"></a>参照  
 [関数 &#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)  
  
  
