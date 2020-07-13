---
title: Analysis Services OLE DB Provider (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services OLE DB Provider
ms.assetid: cdeecd50-1d91-4162-a4a2-01c7799b02a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c0348a23a6def4c3cdbd083354083947ce1390b
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528666"
---
# <a name="analysis-services-ole-db-provider-analysis-services---multidimensional-data"></a>Analysis Services OLE DB Provider (Analysis Services - 多次元データ)
  Analysis Services OLE DB Provider は、と対話するアプリケーションのインターフェイスです [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。 これを使用して、多次元データを扱うクライアント アプリケーションを構築します。 このプロバイダーは、多次元データとリレーショナル データのオンラインやオフラインでのデータ マイニング分析用のメソッドを提供しており、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に含まれています。 サードパーティのクライアント アプリケーションにより、再配布できます。  
  
 キューブやデータ マイニング モデルへの接続、キューブやデータ マイニング モデルへのクエリ、スキーマ情報の取得などのタスクを実行するために [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] と相互作用する場合、基本的には Analysis Services OLE DB Provider が使用されます。  
  
 Analysis Services OLE DB Provider はスタンドアロンのプロバイダーとして機能し、クライアント アプリケーションがリレーショナル ソースや多次元ソースからローカルのキューブ ファイルやマイニング モデルを作成できるようにします。 クライアント アプリケーションは、ローカル キューブに接続して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを実行するフルスケールのサーバーと対話することなく、MDX (多次元式) を使用したクエリを実行できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータアクセス &#40;Analysis Services-多次元データ&#41;](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
