---
title: CALL ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CALL
dev_langs:
- kbMDX
helpviewer_keywords:
- voids [MDX]
- stored procedures [MDX]
- CALL statement
ms.assetid: b534a20b-924c-43b8-832d-24e57d50425c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 079f29676bd1f71d70e182af2ee8664361916d49
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-manipulation---call"></a>MDX データ操作の呼び出し
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>解説  
 **呼び出す**ステートメント、指定した登録されているストアド プロシージャが実行、指定されたストアド プロシージャの 1 つ以上の引数を含めることもできます。 **呼び出す**ステートメントは、白い隙間を返すストアド プロシージャでのみ使用します。 MDX 式の中でこのステートメントと他の関数や演算子を併用することはできません。 値を返す登録済みのストアド プロシージャについては、MDX 式の中で直接呼び出すことも、MDX の他の関数や演算子と併用することも可能です。  
  
 キューブが指定されていない場合は、現在のキューブに対してストアド プロシージャを実行します。  
  
> [!NOTE]  
>  クライアントでは、ストアド プロシージャが登録されていない場合、**呼び出す**ステートメントのインスタンスからストアド プロシージャを呼び出すしようとしました。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [MDX データ操作ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [ストアド プロシージャの使用 &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
