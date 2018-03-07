---
title: "モデル オブジェクト アクセス許可を削除する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c763d1b23676bc36e678e99abbb8a95d47b5d421
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="delete-model-object-permissions-master-data-services"></a>モデル オブジェクト権限を削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデル オブジェクトの権限を削除して、作成されている割り当てを削除します。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-delete-model-object-permissions"></a>モデル オブジェクト権限を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]**をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]**をクリックします。  
  
4.  **[モデル]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します (オプション)。  
  
6.  **[編集]**をクリックします。  
  
7.  **[モデル権限の概要]** 領域で、削除する権限の行を選択します。  
  
     その権限のツリー ノードが特定され、強調表示されます。  
  
8.  ツリー ノードをクリックし、コンテキスト メニューの **[アクセスをクリア]**をクリックします。  
  
9. **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)   
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
