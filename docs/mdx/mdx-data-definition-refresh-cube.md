---
title: REFRESH CUBE ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dafc13dda1f8ecab1400a88d1ca66eff5f317e43
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741731"
---
# <a name="mdx-data-definition---refresh-cube"></a>MDX データ定義の更新キューブ


  キューブのクライアント キャッシュを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 インスタンスに接続されているクライアント アプリケーションの[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、このステートメントにより、サーバーと同期するクライアント アプリケーションでキャッシュされているメモリです。 この検出および更新は日常的かつ自動的に行われますが、同期が行われるまでの時間はクライアント接続文字列の設定によって異なります。 REFRESH CUBE ステートメントを実行すると、データが直ちに更新されます。  
  
 ローカル キューブに接続しているクライアント アプリケーションの場合、REFRESH CUBE ステートメントは、ローカルのキューブ ファイルを再構築します。  
  
> [!IMPORTANT]  
>  サーバーに保存されている名前付きセットは更新されません。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
