---
title: 階層 (Master Data Services) 内のメンバーを移動 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d5e8bf5a041458614422b3c89666ea3ffc9f5a86
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084558"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>階層内のメンバーを移動する (マスター データ サービス)
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で、階層内のメンバーを移動してその場所または親割り当てを変更します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   明示的階層, が必要以上の**更新**エンティティへのアクセスを許可します。  
  
-   派生階層, が必要以上の**更新**モデルを任意のドメイン ベースの属性を階層内で使用します。  
  
### <a name="to-move-members-within-a-hierarchy"></a>階層内のメンバーを移動するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
2.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
3.  **[エクスプローラー]** をクリックします。  
  
4.  メニュー バーのをポイント**階層** をクリック*hierarchy_name*です。  
  
5.  **階層** ウィンドウで、階層を表示する場所をツリー構造で、移動する各メンバーのチェック ボックスをクリックします。  
  
6.  上部にある、**階層** ウィンドウで、をクリックして**切り取り**です。  
  
7.  **階層** ウィンドウで、メンバーの移動先となるメンバーのチェック ボックスをクリックします。  
  
8.  をクリックして**貼り付け**です。  
  
    > [!NOTE]  
    >  派生階層では、メンバーは同じレベルにのみ移動できます。 また、メンバーの並べ替え順序は変更できません。  
  
## <a name="see-also"></a>参照  
 [ステージング処理を使用した明示的階層メンバーの移動&#40;マスター データ サービス&#41;](add-update-and-delete-data-master-data-services.md)   
 [派生階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [明示的階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  