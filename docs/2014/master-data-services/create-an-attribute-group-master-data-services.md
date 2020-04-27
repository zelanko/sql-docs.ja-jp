---
title: 属性グループを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c832fe601eb7151e438d7f93c3e39e9b249ea246
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483318"
---
# <a name="create-an-attribute-group-master-data-services"></a>属性グループを作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** グリッドの個々のタブに属性を表示する場合、属性グループを作成します。  
  
> [!NOTE]  
>  属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。 グループを表示する方法の詳細については、「 [属性グループのユーザーへの表示 (マスター データ サービス)](make-an-attribute-group-visible-to-users-master-data-services.md)機能領域のグリッドの上部にタブとして表示されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも 1 つの属性が必要です。 詳細については、「 [テキスト属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)」を参照してください。  
  
### <a name="to-create-an-attribute-group"></a>属性グループを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  [**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**属性グループ**] をクリックします。  
  
3.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  **[リーフ グループ]**、 **[統合グループ]**、または **[コレクション グループ]** をクリックして、リーフ メンバー、統合メンバー、またはコレクションの属性グループを作成します。  
  
6.  [**属性グループの追加**] をクリックします。  
  
7.  [**リーフグループ名**] ボックスに、グループの名前を入力します。 これは、**エクスプローラー**のタブに表示される名前です。  
  
    > [!NOTE]  
    >  手順 5. で [**統合グループ**] または [**コレクショングループ**] を選択した場合、このボックスはそれぞれ [**統合グループ名**] または [**コレクショングループ名**] になります。  
  
8.  **[グループの保存]** をクリックします。  
  
9. グループのフォルダーを展開します。  
  
10. **[属性]** をクリックします。  
  
11. [**選択したアイテムの編集**] をクリックします。  
  
12. **使用可能な**ボックスの [属性] をクリックし、[**追加**] 矢印をクリックします。 すべてを追加するには、 **[すべて追加]** 矢印をクリックします。  
  
13. 必要に応じて、**上**矢印と**下**矢印をクリックして、属性の順序を左から右に変更します。  
  
14. **[Save]** (保存) をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [属性グループのユーザーへの表示 (マスター データ サービス)](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [属性グループ &#40;マスターデータサービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [属性グループ名を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [属性グループ &#40;マスターデータサービスの削除&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)   
 [リーフアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [統合アクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
