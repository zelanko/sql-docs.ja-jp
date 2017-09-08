---
title: "既定 (Analysis Services) で機能をオフ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4b9d92a7620ed165d661fe4c48726a8049d33500
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="features-off-by-default-analysis-services"></a>既定でオフになっている機能 (Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、既定でセキュリティ保護されるようにデザインされています。 したがって、セキュリティを損なう可能性のある機能は既定では無効になっています。 次の機能は、無効状態でインストールされ、使用するときに明示的に有効にする必要があります。  
  
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
  
  
