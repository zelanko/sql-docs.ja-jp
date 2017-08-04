---
title: "階層メンバー権限 (Master Data Services) を削除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c06cb0309491e9663e4b130b9a641bbbc3a07be
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a>階層メンバーの権限を削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] でモデル オブジェクトの権限を削除して、作成されている割り当てを削除します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-hierarchy-member-permissions"></a>階層メンバーの権限を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]**をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]**をクリックします。  
  
4.  **[階層メンバー]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
6.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
7.  **[編集]**をクリックします。  
  
8.  **[階層メンバーの権限]** パネルで、該当する権限のツリー ノードを見つけます。  
  
9. ツリー ノードをクリックし、コンテキスト メニューで **[なし]** をクリックします。  
  
    > [!NOTE]  
    >  権限がグループから継承されている場合、ユーザーから権限を削除できません。 グループから権限を削除する必要があります。  
  
10. **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [階層メンバーの権限 & #40 です。マスター データ サービス &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [階層メンバーの権限 &#40; を割り当てるマスター データ サービス &#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
