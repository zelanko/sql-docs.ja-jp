---
title: モデルを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
caps.latest.revision: 13
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f1c2cb47c12d162fceb8b0b59fd6d493fbe29195
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-model-master-data-services"></a>モデルを作成する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルを作成してモデル オブジェクトを含めます。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-create-a-model"></a>モデルを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[モデル]** をクリックします。  
  
3.  **[モデルの管理]** ページで **[追加]** をクリックします。 右側にパネルが表示されます。  
  
4.  **[名前]** ボックスに、モデルの名前を入力します。  
  
5.  (必要に応じて) **[説明]** フィールドに、モデルの説明を入力します。  
  
6.  **[Log Retention Days]** (ログの保持日数) フィールドで、ログ データを保持するためのオプションのいずれかを選択します。 既定値は **[システム設定]** です。これは、値が [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]のシステム設定から継承されることを示します。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
     システム設定を上書きし、トランザクション ログ データを削除しない場合は、 **[いいえ]** を選択します。 前の日のログをすべて切り捨てて、今日のログ データのみを保持するには、 **[はい]** を選択し、 **[日間]** フィールドに 0 を設定します。 指定した日数のログ データを保持するには、 **[はい]** を選択し、 **[日間]** フィールドに目的の日数を設定します。  
  
7.  (オプション) **[モデルと同じ名前のエンティティを作成する]** をクリックして、モデルと同じ名前のエンティティを作成します。  
  
8.  **[モデルの保存]** をクリックします。  
  
 作成されたモデルごとに、8 列の行がグリッドに追加されます。 8 つの列は次のとおりです。  
  
-   **[状態]**: モデルの状態。 **[モデルの保存]** ボタンをクリックすると、モデルが更新されていることを示す ![更新中](../master-data-services/media/mds-model-status-updating.png "更新中") 画像が表示されます。 モデルの作成中または編集中にエラーが発生すると、![エラー](../master-data-services/media/mds-model-status-error.png "エラー") 画像が表示されます。 それ以外の場合は正常な状態であり、 ![[OK]](../master-data-services/media/mds-model-status-ok.png "[OK]") 画像が表示されます。  
  
-   **[名前]**: モデル名。  
  
-   **[説明]**: モデルの説明。  
  
-   **[Log Retention Days]**(ログの保持日数): モデルのログを保持する日数。  
  
-   **[作成者]**: モデルを作成したユーザーのユーザー名。  
  
-   **[Created Date and Time]**(作成日時): モデルが作成された日時。  
  
-   **[Updated By]**(更新者): モデルを最後に更新したユーザーのユーザー名。  
  
-   **[Updated Date and Time]**(更新日時): モデルが最後に更新された日時。  
  
## <a name="next-steps"></a>Next Steps  
  
-   [エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [モデル (マスター データ サービス)](../master-data-services/models-master-data-services.md)   
 [エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)   
 [モデルを削除する (マスター データ サービス)](../master-data-services/delete-a-model-master-data-services.md)   
 [モデルを編集する &#40;マスター データ サービス&#41;](../master-data-services/edit-model-master-data-services.md)   
 [トランザクション (マスター データ サービス)](../master-data-services/transactions-master-data-services.md)  
  
  
