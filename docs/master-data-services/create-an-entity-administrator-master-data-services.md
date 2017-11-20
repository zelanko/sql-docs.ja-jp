---
title: "エンティティ管理者を作成する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 717be1e8-488e-4219-8d1e-ca9084b864cd
caps.latest.revision: 5
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: b322107b8fa557d82b03a6b08b96c872be5205af
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="create-an-entity-administrator-master-data-services"></a>エンティティ管理者を作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、グループまたはユーザーに 1 つ以上のエンティティのすべてのオブジェクトに対してすべての権限を付与する、待機中の変更セットを承認する権限を付与するには、エンティティ管理者を作成します。  
  
> [!TIP]  
>  管理を簡素化するために、Windows グループまたはローカル グループを作成し、そのグループをエンティティ管理者として構成します。 また、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
## <a name="to-create-an-entity-administrator"></a>エンティティ管理者を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]**をクリックします。  
  
2.  編集するユーザーまたはグループの行を選択し、 **[選択したユーザーの編集]**をクリックします。  
  
3.  **[モデル]** タブをクリックし、必要に応じて **[モデル]** の一覧からモデルを選択して、 **[編集]**をクリックします。  
  
4.  権限を付与するエンティティをクリックし、メニューで **[管理者]** をクリックします。  
  
5.  グループまたはユーザーを管理者にする各エンティティについて、手順 4 を実行します。  
  
6.  **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)   
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [階層メンバーの権限を割り当てる (マスター データ サービス)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  

