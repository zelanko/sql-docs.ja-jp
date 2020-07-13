---
title: モデル管理者を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0d4a9e07006444cf85a6d453e6dc8e2956d55e78
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971822"
---
# <a name="create-a-model-administrator-master-data-services"></a>モデル管理者を作成する (マスター データ サービス)
  で [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 、1つまたは複数のモデルのすべてのオブジェクトに対する**更新**権限をグループまたはユーザーに付与する場合は、モデル管理者を作成します。  
  
> [!TIP]  
>  管理を簡略化するには、Windows グループまたはローカルグループを作成し、モデル管理者として構成します。 また、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-create-a-model-administrator"></a>モデル管理者を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]** をクリックします。  
  
4.  **[モデル]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します (オプション)。  
  
6.  **[編集]** をクリックします。  
  
7.  権限を与えるモデルをクリックします。  
  
8.  メニューから [**更新**] を選択します。  
  
9. グループまたはユーザーを管理者にする各モデルについて、手順 7 と 8 を実行します。  
  
10. **[保存]** をクリックします。  
  
## <a name="remarks"></a>注釈  
 モデル オブジェクトまたは階層メンバーに他の権限を割り当てないでください。 この場合、ユーザーは管理者ではなくなり、[**エクスプローラー**] 以外の機能領域でモデルを表示することはできません。  
  
 例外が1つあります。ユーザーが [**階層メンバー** ] タブで階層の**ルート**に割り当てられた**更新**権限を持っている場合、そのユーザーは引き続きモデル管理者と見なされます。  
  
## <a name="see-also"></a>参照  
 [管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)   
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [階層メンバーの権限を割り当てる &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
