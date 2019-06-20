---
title: REFRESH CUBE ステートメント (MDX) |Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285079"
---
# <a name="mdx-data-definition---refresh-cube"></a>MDX データ操作 - REFRESH CUBE


  キューブのクライアント キャッシュを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式。  
  
## <a name="remarks"></a>コメント  
 インスタンスに接続されているクライアント アプリケーションの[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、このステートメントは、サーバーと同期するクライアント アプリケーションのキャッシュ メモリをによりします。 この検出および更新は日常的かつ自動的に行われますが、同期が行われるまでの時間はクライアント接続文字列の設定によって異なります。 REFRESH CUBE ステートメントは、データをすぐに更新します。  
  
 ローカル キューブに接続されている、クライアント アプリケーションは、REFRESH CUBE ステートメントは、再構築するローカル キューブ ファイルをさせます。  
  
> [!IMPORTANT]  
>  サーバーに保存されている名前付きセットは更新されません。  
  
## <a name="see-also"></a>関連項目  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
