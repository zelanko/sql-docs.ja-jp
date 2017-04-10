---
title: "モデルを編集する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "モデル [マスター データ サービス], 名前の変更"
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# モデルを編集する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデルの名前と説明を変更し、トランザクション ログを保持する日数を指定できます。  
  
 詳細については、「[トランザクション (マスター データ サービス)](../master-data-services/transactions-master-data-services.md)」を参照してください。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### モデルを変更するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[モデル]**をクリックします。  
  
3.  **[モデルの管理]** ページで、グリッドから、モデルの名前または説明を変更する行を選択します。  
  
4.  **[編集]**をクリックします。  
  
5.  **[名前]** ボックスに、モデルの新しい名前を入力します。  
  
6.  **[説明]** フィールドに、モデルの新しい説明を入力します。  
  
7.  **[Log Retention Days]** (ログの保持日数) フィールドで、ログ データを保持するためのオプションのいずれかを選択します。 既定値は **[システム設定]**です。これは、値が [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]のシステム設定から継承されることを示します。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
     システム設定を上書きし、トランザクション ログ データを削除しない場合は、 **[いいえ]**を選択します。 前の日のログをすべて切り捨てて、今日のログ データのみを保持するには、 **[はい]** を選択し、 **[日間]** フィールドに 0 を設定します。 指定した日数のログ データを保持するには、 **[はい]** を選択し、 **[日間]** フィールドに目的の日数を設定します。  
  
8.  **[モデルの保存]**をクリックします。  
  
 グリッドの **[状態]** 列には、モデルに対する操作の状態が示されます。 **[モデルの保存]** ボタンをクリックすると、モデルが更新されていることを示す ![Updating](../master-data-services/media/mds-model-status-updating.png "Updating") 画像が表示されます。 モデルを作成または編集中にエラーが発生すると、![Error](../master-data-services/media/mds-model-status-error.png "Error") 画像が表示されます。 それ以外の場合は正常な状態であり、![OK](../master-data-services/media/mds-model-status-ok.png "OK") 画像が表示されます。  
  
## 参照  
 [モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)   
 [モデルを削除する (マスター データ サービス)](../master-data-services/delete-a-model-master-data-services.md)   
 [モデル (マスター データ サービス)](../master-data-services/models-master-data-services.md)  
  
  