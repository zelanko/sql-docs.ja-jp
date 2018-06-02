---
title: CLEAR CALCULATIONS ステートメント (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f210f2ad8af7b0d4e71482946a496d326fe63f24
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579784"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>MDX データ操作 - CLEAR CALCULATIONS 
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  キューブからすべての計算を削除して、キューブの計算パスを 0 に戻します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Expression*  
 有効な多次元式 (MDX) キューブ式です。  
  
## <a name="remarks"></a>コメント  
 **FROM**キューブのコンテキストが MDX スクリプトなど、既知の場合、句を省略できます。  
  
> [!NOTE]  
>  このステートメントは、サーバー管理者やデータベース管理者、またはキューブのソース データにアクセスできるロールのメンバー (つまり、ReadSourceData=true) のみが実行できます。  
  
## <a name="see-also"></a>参照  
 [MDX データ操作ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
