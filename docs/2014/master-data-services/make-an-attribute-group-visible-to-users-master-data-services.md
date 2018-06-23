---
title: 属性グループのユーザーへの表示 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 70dcc1e8f35f288b4693bd87308d7f2abcff0136
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163889"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a>属性グループのユーザーへの表示 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** 機能領域のグリッドの上部にタブを表示させる場合は、ユーザーまたはグループに対して属性グループを表示します。  
  
 属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも 1 つの属性グループが必要です。 詳細については、「[属性グループを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)」を参照してください。  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a>属性グループをユーザーに表示するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **モデルビュー**  ページで、メニュー バーのをポイント**管理** をクリック**属性グループ**です。  
  
3.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  展開するプラス記号をクリックして**リーフ グループ**、**統合グループ**、または**コレクション グループ**、表示されるようにするグループの種類によって異なります。  
  
6.  プラス記号をクリックして、表示するグループを展開します。  
  
7.  いずれかをクリックして**ユーザー**または**グループ**にするかどうかをグループを表示するユーザーまたはグループに依存します。  
  
8.  をクリックして**選択した項目を編集**です。  
  
9. ユーザーまたはグループをクリックして、**利用可能**ボックス、をクリックし、**追加**矢印です。 すべてを追加するには、 **[すべて追加]** 矢印をクリックします。  
  
10. **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性グループ&#40;マスター データ サービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [属性グループを作成&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  