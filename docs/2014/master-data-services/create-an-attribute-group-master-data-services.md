---
title: 属性グループを作成する (マスター データ サービス) | Microsoft Docs
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
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0a063af91090ff2e8d5eb1145bb5968573d04523
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165897"
---
# <a name="create-an-attribute-group-master-data-services"></a>属性グループを作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** グリッドの個々のタブに属性を表示する場合、属性グループを作成します。  
  
> [!NOTE]  
>  属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。 詳細については、グループを表示する、次を参照してください。 [、ユーザーが、属性グループ表示&#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)です。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも 1 つの属性が必要です。 詳細については、「[テキスト属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)」を参照してください。  
  
### <a name="to-create-an-attribute-group"></a>属性グループを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **モデルビュー**  ページで、メニュー バーのをポイント**管理** をクリック**属性グループ**です。  
  
3.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  **[リーフ グループ]**、 **[統合グループ]**、または **[コレクション グループ]** をクリックして、リーフ メンバー、統合メンバー、またはコレクションの属性グループを作成します。  
  
6.  をクリックして**属性グループの追加**です。  
  
7.  **リーフ グループ名**ボックスに、グループの名前を入力します。 これは、タブで表示される名前**エクスプ ローラー**です。  
  
    > [!NOTE]  
    >  選択した場合は**統合グループ**または**コレクション グループ**このボックスは、手順 5. で**統合グループ名**または**コレクション グループ名**、それぞれします。  
  
8.  **[グループの保存]** をクリックします。  
  
9. グループのフォルダーを展開します。  
  
10. **[属性]** をクリックします。  
  
11. をクリックして**選択した項目を編集**です。  
  
12. 属性をクリックして、**利用可能**ボックス、をクリックし、**追加**矢印です。 すべてを追加するには、 **[すべて追加]** 矢印をクリックします。  
  
13. 必要に応じて、をクリックして、**を**と**ダウン**矢印属性の左から右の順序を変更します。  
  
14. **[保存]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [属性グループをユーザーに表示されるように&#40;マスター データ サービス&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [属性グループ&#40;マスター データ サービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [属性&#40;マスター データ サービス&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [属性グループ名を変更する &#40;マスター データ サービス&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [属性グループを削除する &#40;マスター データ サービス&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)   
 [アクセス許可は、リーフ&#40;マスター データ サービス&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [アクセス許可を統合&#40;マスター データ サービス&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  