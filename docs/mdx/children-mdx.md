---
title: 子 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0af4d7b97777002dc5683c075f82531ccc8df86e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016799"
---
# <a name="children-mdx"></a>Children (MDX)


  指定されたメンバーの子のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **Children**関数は、指定されたメンバーの子を含む自然な順序付けされたセットを返します。 指定されているメンバーに子メンバーがない場合、この関数は空のセットを返します。  
  
## <a name="example"></a>例  
 次の例では、geography ディメンションの Geography 階層の米国メンバーの子を返します。  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、列軸上の**Measures**ディメンションのすべてのメンバーを返します。これには、すべての計算される`[Product].[Model Name]`メンバーと、 **Adventure works**キューブの行軸にある属性階層のすべての子のセットが含まれます。  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|リリース|履歴|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**変更内容 :**<br /> -わかりやすくするために、構文と引数を更新しました。<br /><br /> -更新された例を追加しました。|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
