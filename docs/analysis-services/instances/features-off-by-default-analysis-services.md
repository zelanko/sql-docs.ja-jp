---
title: "既定 (Analysis Services) で機能をオフ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 21ff5e0b59b3e14df550bb580b1c59dde449452e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="features-off-by-default-analysis-services"></a>既定でオフになっている機能 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]インスタンス[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は既定ではセキュリティで保護するよう設計されています。 したがって、セキュリティを損なう可能性のある機能は既定では無効になっています。 次の機能は、無効状態でインストールされ、使用するときに明示的に有効にする必要があります。  
  
## <a name="feature-list"></a>機能一覧  
 次の機能を有効にするには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に接続します。 インスタンス名を右クリックして、 **[ファセット]**を選択します。 または、次のセクションで説明するように、これらの機能をサーバー プロパティを通して有効にすることができます。  
  
-   アドホック データ マイニング (OpenRowset) クエリ  
  
-   リンク オブジェクト (リンク先)  
  
-   リンク オブジェクト (リンク元)  
  
-   ローカル接続のみのリッスン  
  
-   ユーザー定義関数  
  
## <a name="server-properties"></a>サーバー プロパティ  
 既定でオフになっている追加の機能はサーバー プロパティを通して有効にすることができます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に接続します。 インスタンス名を右クリックして、 **[プロパティ]**を選択します。 **[全般]**をクリックしてから、 **[詳細の表示]** をクリックして、より大きなプロパティ一覧を表示します。  
  
-   アドホック データ マイニング (OpenRowset) クエリ  
  
-   セッション マイニング モデルを許可 (データ マイニング)  
  
-   リンク オブジェクト (リンク先)  
  
-   リンク オブジェクト (リンク元)  
  
-   COM ベースのユーザー定義関数  
  
-   フライト レコーダーのトレース定義 (テンプレート)  
  
-   クエリ ログ  
  
-   ローカル接続のみのリッスン  
  
-   バイナリ XML  
  
-   圧縮  
  
-   グループ アフィニティ。 詳細については、「 [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) 」を参照してください。  
  
  
