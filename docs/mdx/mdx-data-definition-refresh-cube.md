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
ms.openlocfilehash: 957609573c206b7c3492789c369d0fb2be2398a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038163"
---
# <a name="mdx-data-definition---refresh-cube"></a>MDX データ操作 - REFRESH CUBE


  キューブのクライアントキャッシュを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式です。  
  
## <a name="remarks"></a>Remarks  
 の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスに接続されているクライアントアプリケーションの場合、このステートメントによって、クライアントアプリケーションでキャッシュされたメモリがサーバーと同期されます。 この検出および更新は日常的かつ自動的に行われますが、同期が行われるまでの時間はクライアント接続文字列の設定によって異なります。 REFRESH CUBE ステートメントは、すぐにデータを更新します。  
  
 ローカルキューブに接続されているクライアントアプリケーションの場合、REFRESH CUBE ステートメントを使用すると、ローカルキューブファイルが再構築されます。  
  
> [!IMPORTANT]  
>  サーバーに格納されている名前付きセットは更新されません。  
  
## <a name="see-also"></a>参照  
 [Mdx&#41;&#40;mdx データ定義ステートメント](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
