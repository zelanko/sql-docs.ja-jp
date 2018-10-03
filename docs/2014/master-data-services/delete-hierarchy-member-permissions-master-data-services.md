---
title: 階層メンバーのアクセス許可を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ca4e921f5bff1f9870b812958baa63df1caedc32
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093722"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a>階層メンバーの権限を削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデル オブジェクトの権限を削除して、作成されている割り当てを削除します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-hierarchy-member-permissions"></a>階層メンバーの権限を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]** をクリックします。  
  
4.  **[階層メンバー]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
6.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
7.  **階層メンバー権限の概要**ウィンドウで、削除する権限の行を選択します。  
  
8.  クリックして**選択されたアクセス許可を削除**します。  
  
    > [!NOTE]  
    >  権限がグループから継承されている場合、ユーザーから権限を削除できません。 グループから権限を削除する必要があります。  
  
## <a name="see-also"></a>参照  
 [階層メンバーの権限&#40;マスター データ サービス&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [階層メンバー権限を割り当てる&#40;マスター データ サービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
