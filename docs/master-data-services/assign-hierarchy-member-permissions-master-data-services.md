---
title: 階層メンバーのアクセス許可を割り当てる (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b417365e74eed99b0598eff878157309254e3fb1
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>階層メンバーの権限を割り当てる (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  階層メンバーに権限を割り当てて、 **の** [エクスプローラー] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域にあるデータを表示するためのアクセス権をユーザーまたはグループに付与します。  
  
 階層メンバーの権限はオプションです。 階層メンバーの権限は、必須であるモデル オブジェクトの権限に粒度を追加します。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-assign-hierarchy-member-permissions"></a>階層メンバーの権限を割り当てるには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]** をクリックします。  
  
4.  **[階層メンバー]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
6.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
7.  **[階層]** ボックスの一覧から階層を選択します。  
  
8.  **[編集]** をクリックします。  
  
9. ツリーを展開して、権限を割り当てる階層ノードをクリックします。  
  
10. メニューから、 **作成**、 **読み取り、更新** 、および **削除** 権限の組み合わせ、または **拒否** 権限を選択します。  
  
11. **[保存]** をクリックします。  
  
    > [!NOTE]  
    >  階層メンバーの権限は、すぐには有効になりません。 詳細については、「[メンバー権限を直ちに適用する (マスター データ サービス)](../master-data-services/immediately-apply-member-permissions-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [階層メンバーの権限を削除する (マスター データ サービス)](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
