---
title: CALL ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4052134e9fd7d3c6877894c61480897e40982b59
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741961"
---
# <a name="mdx-data-manipulation---call"></a>MDX データ操作 - CALL


  現在のスコープで、または指定されたキューブに対して、void を返すストアド プロシージャを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>引数  
 *SP_Name*  
 ストアド プロシージャの名前を指定する有効な文字列式です。  
  
 *SP_Argument*  
 呼び出したストアド プロシージャに渡す引数を指定する有効な文字列式です。  
  
 *Cube_Expression*  
 キューブの名前を指定する有効な文字列キューブ式です。  
  
## <a name="remarks"></a>コメント  
 **呼び出す**ステートメント、指定した登録されているストアド プロシージャが実行、指定されたストアド プロシージャの 1 つ以上の引数を含めることもできます。 **呼び出す**ステートメントは、白い隙間を返すストアド プロシージャでのみ使用します。 MDX 式の中でこのステートメントと他の関数や演算子を併用することはできません。 値を返す登録済みのストアド プロシージャについては、MDX 式の中で直接呼び出すことも、MDX の他の関数や演算子と併用することも可能です。  
  
 キューブが指定されていない場合は、現在のキューブに対してストアド プロシージャを実行します。  
  
> [!NOTE]  
>  クライアントでは、ストアド プロシージャが登録されていない場合、**呼び出す**ステートメントのインスタンスからストアド プロシージャを呼び出すしようとしました。[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [MDX データ操作ステートメント &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [ストアド プロシージャの使用 &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
