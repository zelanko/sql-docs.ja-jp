---
title: "モデル管理者を作成する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
caps.latest.revision: "6"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57ece5701f4d4273d0130e72542090bc9d4fcc57
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-model-administrator-master-data-services"></a>モデル管理者を作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、1 つ以上のモデルに含まれるすべてのオブジェクトに対するすべての権限をグループまたはユーザーに与える場合にモデル管理者を作成します。  
  
> [!TIP]  
>  管理を簡素化するために、Windows グループまたはローカル グループを作成し、そのグループをモデル管理者として構成します。 また、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-create-a-model-administrator"></a>モデル管理者を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]**をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]**をクリックします。  
  
4.  **[モデル]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します (オプション)。  
  
6.  **[編集]**をクリックします。  
  
7.  権限を与えるモデルをクリックします。  
  
8.  メニューから **[管理者]**を選択します。  
  
9. グループまたはユーザーを管理者にする各モデルについて、手順 7 と 8 を実行します。  
  
10. **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)   
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [階層メンバーの権限を割り当てる (マスター データ サービス)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
