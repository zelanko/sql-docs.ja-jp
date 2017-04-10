---
title: "メンバー リビジョン履歴 (マスター データ サービス) | Microsoft Docs"
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
ms.assetid: 113069c5-12e6-48ec-b443-b42e14f77308
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# メンバー リビジョン履歴 (マスター データ サービス)
  メンバー リビジョン履歴は、エンティティのトランザクション ログの種類がメンバーの場合、メンバーに変更が加えられるたびに記録されます。  
  
 トランザクション ログの種類については、「[エンティティのトランザクション ログの種類の変更 (マスター データ サービス)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)」を参照してください。  
  
 メンバー リビジョン履歴は、次の変更が行われた場合に記録されます。  
  
-   メンバーが作成、削除、再アクティブ化、またはパージされた。  
  
-   属性値が変更された。  
  
-   メンバーが階層内またはコレクション内で移動された。  
  
## エンティティ単位でのリビジョン履歴の表示と管理  
 [エクスプローラー] 機能領域で、エンティティ内のすべてのメンバーのリビジョンを表示できます。 更新権限を持っている場合、メンバーを以前のリビジョンにロールバックできます。  
  
 **リビジョン履歴を表示して管理するには**  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルとバージョンを選択し、 **[エクスプローラー]**をクリックします。  
  
2.  **[エンティティ]** メニューからエンティティを選択します。  
  
3.  **[履歴の表示]** をクリックして、エンティティの履歴データをすべて表示します。  
  
4.  **[フィルター]** をクリックしてデータをフィルター処理します。  
  
5.  列ヘッダーをクリックしてデータを並べ替えます。  
  
6.  更新権限を持っている場合、 **[Revert Member]** (メンバーを元に戻す) をクリックして、選択したバージョンにロールバックします。  
  
## メンバー単位でのリビジョン履歴の表示と管理  
 メンバーに対する読み取り権限を持っている場合、[エクスプローラー] 機能領域でメンバーのリビジョンを表示できます。 更新権限を持っている場合、メンバーをロールバックして以前のバージョンに戻したり、リビジョンに注釈を追加したりできます。  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルとバージョンを選択し、 **[エクスプローラー]**をクリックします。  
  
2.  **[エンティティ]** メニューからエンティティを選択します。  
  
3.  メンバーを選択します。  
  
4.  右側のペインで **[履歴の表示]** をクリックします。  
  
## ログの保有期間の設定  
 **データベースのシステム設定の** [Log retention in Days] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] (ログ保有期間日数) プロパティを設定することで、履歴データが保持される期間を構成できます。または、モデルを作成または編集するときに、**[Log Retention Days]** (ログ保有期間の日数) を設定して保有期間を構成できます。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|メンバー リビジョン履歴のロールバック|[メンバー リビジョン履歴のロールバック (マスター データ サービス)](../master-data-services/rollback-member-revision-history-master-data-services.md)|  
  
## 参照  
 [モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)   
 [システム設定 (マスター データ サービス)](../master-data-services/system-settings-master-data-services.md)  
  
  