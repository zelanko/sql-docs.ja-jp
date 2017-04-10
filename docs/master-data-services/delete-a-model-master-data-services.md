---
title: "モデルを削除する (マスター データ サービス) | Microsoft Docs"
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
  - "モデルの削除 [マスター データ サービス]"
  - "モデル [マスター データ サービス], モデルの削除"
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# モデルを削除する (マスター データ サービス)
  モデルを削除して、モデルおよびそのすべてのデータを [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] から削除します。  
  
> [!NOTE]  
>  これらの手順が完了すると、モデルのすべてのバージョンのすべてのオブジェクトおよびすべてのデータが完全に削除されます。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### モデルを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[モデル]**をクリックします。  
  
3.  **[モデルの管理]** ページで、グリッドから削除するモデルの行を選択します。  
  
4.  **[削除]**をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
6.  追加の確認のダイアログ ボックスで **[OK]** をクリックします。  
  
 グリッドの **[状態]** 列には、モデルに対する操作の状態が示されます。 **[モデルの保存]** ボタンをクリックすると、モデルが更新されていることを示す ![Updating](../master-data-services/media/mds-model-status-updating.png "Updating") 画像が表示されます。 モデルを作成または編集中にエラーが発生すると、![Error](../master-data-services/media/mds-model-status-error.png "Error") 画像が表示されます。 それ以外の場合は正常な状態であり、![OK](../master-data-services/media/mds-model-status-ok.png "OK") 画像が表示されます。  
  
## 参照  
 [モデル (マスター データ サービス)](../master-data-services/models-master-data-services.md)   
 [モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)  
  
  