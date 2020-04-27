---
title: 属性グループのユーザーへの表示 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 97cc4c9955b64583571a63fa72df4663c1acd812
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479152"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a>属性グループのユーザーへの表示 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** 機能領域のグリッドの上部にタブを表示させる場合は、ユーザーまたはグループに対して属性グループを表示します。  
  
 属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも 1 つの属性グループが必要です。 詳細については、「 [属性グループを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)」を参照してください。  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a>属性グループをユーザーに表示するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  [**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**属性グループ**] をクリックします。  
  
3.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  表示するグループの種類に応じて、プラス記号をクリックして [**リーフグループ**]、[**統合グループ**]、または [**コレクショングループ**] を展開します。  
  
6.  プラス記号をクリックして、表示するグループを展開します。  
  
7.  グループをユーザーとグループのどちらに表示するかに応じて、[**ユーザー** ] または [**グループ**] をクリックします。  
  
8.  [**選択したアイテムの編集**] をクリックします。  
  
9. **使用可能な**ボックスで [ユーザーまたはグループ] をクリックし、[**追加**] 矢印をクリックします。 すべてを追加するには、 **[すべて追加]** 矢印をクリックします。  
  
10. **[Save]** (保存) をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性グループ &#40;マスターデータサービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [属性グループを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
