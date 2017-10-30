---
title: "属性グループのユーザーへの表示 (マスター データ サービス) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: e3922c3ad81de37e73f08bd840def40146c8bf12
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a>属性グループのユーザーへの表示 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** 機能領域のグリッドの上部にタブを表示させる場合は、ユーザーまたはグループに対して属性グループを表示します。  
  
 属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも 1 つの属性グループが必要です。 詳細については、「 [属性グループを作成する (マスター データ サービス)](../master-data-services/create-an-attribute-group-master-data-services.md)」を参照してください。  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a>属性グループをユーザーに表示するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、属性グループを編集するエンティティの行をグリッドから選択します。  
  
4.  **[属性グループ]**をクリックします。  
  
5.  **[属性グループの管理]** ページで、 **[メンバーの種類]** ドロップダウン リスト ボックスからメンバーの種類を選択し、表示するグループの種類に応じて **[リーフ]**、 **[統合]** 、 **[コレクション]**を展開します。  
  
6.  編集する属性グループをグリッドから選択し、 **[編集]**をクリックします。  
  
7.  **[使用可能]** ボックスのユーザーまたはグループをクリックして、 **[追加]** 矢印をクリックします。 すべてを追加するには、 **[すべて追加]** 矢印をクリックします。  
  
8.  **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性グループ (マスター データ サービス)](../master-data-services/attribute-groups-master-data-services.md)   
 [属性グループを作成する (マスター データ サービス)](../master-data-services/create-an-attribute-group-master-data-services.md)  
  
  

