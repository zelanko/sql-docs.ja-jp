---
title: ストアド プロシージャ (MDX) を使用して |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed9232137bcfed47852086ab1b6b76bc2bc2cb69
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582244"
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
  
  
