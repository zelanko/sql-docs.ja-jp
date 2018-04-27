---
title: エンティティを編集する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
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
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 110c7e1af8efb71dfeda95e6940c9fdca0c1b8b7
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="edit-an-entity-master-data-services"></a>エンティティを編集する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、エンティティを編集することができます。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-edit-an-entity"></a>エンティティを編集するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]** をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、変更するエンティティの行をグリッドから選択し、 **[編集]** をクリックします。  
  
4.  **[名前]** ボックスに、エンティティの新しい名前を入力します。  
  
5.  **[説明]** フィールドに、エンティティの新しい説明を入力します。  
  
6.  **[ステージング テーブルの名前]** フィールドに、ステージング テーブルの新しい名前を入力します。  
  
7.  **[トランザクション ログの種類]** フィールドで、ドロップダウン リストから新しいトランザクション ログの種類を選択します。  
  
     詳細については、「[エンティティのトランザクション ログの種類の変更 (マスター データ サービス )](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)」を参照してください。  
  
8.  **[コードの値を自動的に作成]** チェックボックスをオンまたはオフにします。  
  
     詳細については、「[コードの自動作成 (マスター データ サービス)](../master-data-services/automatic-code-creation-master-data-services.md)」を参照してください。  
  
9. **[データ圧縮を有効にする]** チェックボックスをオンまたはオフにします。 既定では、行の圧縮は有効になっています。  
  
     詳細については、「 [Data Compression](../relational-databases/data-compression/data-compression.md)」をご覧ください。  
  
## <a name="status"></a>状態  
 グリッドの状態列には、エンティティに対する操作の状態が示されます。 **[エンティティの保存]** をクリックすると、エンティティが更新中であることを示す次の画像が表示されます。  
  
 ![更新中状態のアイコン](../master-data-services/media/mds-statusicon-updating.png "更新中状態のアイコン")  
  
 エンティティの作成または編集中にエラーが発生すると、次の画像が表示されます。  
  
 ![エラー状態のアイコン](../master-data-services/media/mds-statusicon-error.png "エラー状態のアイコン")  
  
 適切な状態のときは、次の画像が表示されます。  
  
 ![適切な状態のアイコン](../master-data-services/media/mds-statusicon-ok.png "適切な状態のアイコン")  
  
## <a name="see-also"></a>参照  
 [明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [エンティティを削除する (マスター データ サービス)](../master-data-services/delete-an-entity-master-data-services.md)   
 [エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)  
  
  
