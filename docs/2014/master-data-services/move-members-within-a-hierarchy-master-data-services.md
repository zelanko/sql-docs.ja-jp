---
title: 階層内のメンバーを移動する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 58b39d2dc660fd51d1ba21308ff056874a239731
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054088"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>階層内のメンバーを移動する (マスター データ サービス)
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で、階層内のメンバーを移動してその場所または親割り当てを変更します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   明示的階層の場合は、エンティティに対する**更新**権限が最低限必要です。  
  
-   派生階層の場合、モデルと、階層で使用されるドメインベースの属性を**更新**する必要があります。  
  
### <a name="to-move-members-within-a-hierarchy"></a>階層内のメンバーを移動するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
2.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
3.  **[エクスプローラー]** をクリックします。  
  
4.  メニューバーの [**階層**] をポイントし、[ *hierarchy_name*] をクリックします。  
  
5.  階層がツリー構造で表示されている [**階層**] ペインで、移動する各メンバーのチェックボックスをオンにします。  
  
6.  **階層**ペインの上部にある [**切り取り**] をクリックします。  
  
7.  [**階層**] ペインで、メンバーの移動先となるメンバーのチェックボックスをオンにします。  
  
8.  [**貼り付け**] をクリックします。  
  
    > [!NOTE]  
    >  派生階層では、メンバーは同じレベルにのみ移動できます。 また、メンバーの並べ替え順序は変更できません。  
  
## <a name="see-also"></a>参照  
 [ステージングプロセス &#40;マスターデータサービスを使用して明示的階層メンバーを移動する&#41;](add-update-and-delete-data-master-data-services.md)   
 [派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [明示的階層 (マスター データ サービス)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
