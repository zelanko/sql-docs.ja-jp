---
title: IsEmpty (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b31b884e0f86bf2aebe4859cd1c7a441669e813
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905991"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)


  評価した式が空のセル値かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Value_Expression*  
 有効な多次元式 (MDX) 式です。通常は、メンバーまたは組のセル座標を返します。  
  
## <a name="remarks"></a>解説  
 **IsEmpty**関数は、評価された式が空のセル値の場合に**true**を返します。 それ以外の場合、この関数は**false**を返します。  
  
> [!NOTE]  
>  メンバーの既定のプロパティは、そのメンバーの値です。  
  
 空**** のセルの値はで[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]特別な意味を持つため、IsEmpty 関数は空のセルを確実にテストする唯一の方法です。  
  
> [!IMPORTANT]  
>  値式の評価でエラーが返された場合、関数は**false**を返します。 値式がエラーを返すのは、たとえば、プロパティ参照によって、無効なプロパティまたは存在しないプロパティが参照されているような場合です。  
  
 空のセルの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="example"></a>例  
 次の例では、Date ディメンションの Fiscal 階層にある現在のメンバーの Internet Sales Amount が空のセルを返す場合、TRUE を返します。  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [空の値の操作](../mdx/working-with-empty-values.md)   
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
