---
title: ストアドプロシージャの使用 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4daa38f185569e1579413870cc929a8b1b3b6570
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038007"
---
# <a name="using-stored-procedures-mdx"></a>ストアド プロシージャの使用 (MDX)


  .NET ストアド プロシージャやユーザー定義関数を記述して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] および多次元式 (MDX) の機能を拡張できます。 詳細については、「 [ADOMD.NET Server プログラミング](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)」を参照してください。  
  
 ストアドプロシージャを参照したり呼び出したりする場合は、関数名の後にかっこを指定します。 かっこ内で、パラメーターに渡されるデータを提供する引数と呼ばれる式を指定できます。 関数を呼び出す場合は、すべてのパラメーターに引数の値を指定する必要があります。また、パラメーターがユーザー定義関数で定義されているのと同じ順序で引数値を指定する必要があります。  
  
 次のクエリでは、SampleAssembly という名前のアセンブリが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーに登録されていることを前提としています。  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *ストアドプロシージャ*は、これらの種類[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の関数で使用される用語です。 以前のバージョン[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のでは、これらの型の関数を*ユーザー定義関数*と呼びました。  
  
## <a name="types-of-stored-procedures"></a>ストアドプロシージャの種類  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は COM アセンブリと CLR アセンブリの両方をサポートします。 Clr アセンブリで使用可能なセキュリティが強化されているため、CLR アセンブリを使用することをお勧めします。 サーバーに Microsoft Office Excel がインストールされている場合、Excel 関数も使用可能です。  
  
> [!NOTE]  
>  Microsoft Visual Basic for Applications (VBA) COM アセンブリは自動的に登録されます。  
  
## <a name="see-also"></a>参照  
 [関数 &#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)  
  
  
