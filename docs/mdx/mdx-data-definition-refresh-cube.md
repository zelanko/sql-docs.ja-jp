---
title: REFRESH CUBE ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Cube
- REFRESH CUBE
- REFRESH_CUBE
- REFRESH
dev_langs:
- kbMDX
helpviewer_keywords:
- cubes [Analysis Services], cache
- refreshing cache
- REFRESH CUBE statement
- cache [Analysis Services]
ms.assetid: b8c087fb-5d17-4b13-b7cf-9929e9aab35c
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 47bb32f3319e4e184637c3b816f10ca563d6c76d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---refresh-cube"></a>MDX データ定義の更新キューブ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  キューブのクライアント キャッシュを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 インスタンスに接続されているクライアント アプリケーションの[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、このステートメントにより、サーバーと同期するクライアント アプリケーションでキャッシュされているメモリです。 この検出および更新は日常的かつ自動的に行われますが、同期が行われるまでの時間はクライアント接続文字列の設定によって異なります。 REFRESH CUBE ステートメントを実行すると、データが直ちに更新されます。  
  
 ローカル キューブに接続しているクライアント アプリケーションの場合、REFRESH CUBE ステートメントは、ローカルのキューブ ファイルを再構築します。  
  
> [!IMPORTANT]  
>  サーバーに保存されている名前付きセットは更新されません。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
