---
title: "グループを削除する属性 (マスター データ サービス) |Microsoft ドキュメント"
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
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d0f472ad35afbf5a7f881638560338e1bf5900c3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="delete-an-attribute-group-master-data-services"></a>属性グループを削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]の **[エクスプローラー]** 機能領域にタブを表示する必要がなくなった属性グループを削除します。  
  
-   **注** 属性グループが存在する場合、いずれの属性グループにも属さない属性は **[エクスプローラー]**に表示されません。 属性グループが存在しない場合、すべての属性が表示されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-an-attribute-group"></a>属性グループを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、属性グループを編集するエンティティの行をグリッドから選択します。  
  
4.  **[属性グループ]**をクリックします。  
  
5.  **[属性グループの管理]** ページで、 **[メンバーの種類]** ドロップダウン リストからメンバーの種類を選択し、削除するグループの種類に応じて **[リーフ]**、 **[統合]**、 **[コレクション]**を展開します。  
  
6.  削除する属性グループをクリックします。  
  
7.  **[削除]**をクリックします。  
  
8.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性グループ & #40 です。マスター データ サービス &#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [属性グループ &#40; を作成します。マスター データ サービス &#41;](../master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
