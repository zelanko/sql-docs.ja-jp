---
title: インデックスを作成する (マスター データ サービス) | Microsoft Docs
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
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6644098c2dead63de2f68c2ec04c93b0d13a3158
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="create-an-index-master-data-services"></a>インデックスを作成する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  頻繁にクエリを実行する属性の一覧にカスタム インデックスを作成して、クエリのパフォーマンスを高めます。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
 **インデックスを作成するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]** をクリックします。  
  
2.  **[Manage Model]** (モデルの管理) ページでグリッドからモデルを選択し、 **[エンティティ]** をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、インデックスを作成するエンティティの行を **グリッド** から選択します。  
  
4.  **[インデックス]** をクリックします。  
  
5.  **[名前]** ボックスに、このインデックスの名前を入力します。  
  
6.  一意なインデックスを作成する場合は、 **[Is Unique]** (一意) を選択します。 インデックスの種類の詳細については、「 [カスタム インデックス (マスター データ サービス)](../master-data-services/custom-index-master-data-services.md)」を参照してください。  
  
7.  **[使用できる属性]** ボックスの属性をクリックし、 **[追加]** 矢印をクリックします。 すべての属性を追加するには、 **[すべて追加]** 矢印をクリックします。  
  
8.  **[保存]** をクリックします。  
  
 作成されたインデックスごとに、4 列の行がグリッドに追加されます。 次の表で各列について説明します。  
  
|列名|Description|  
|-----------------|-----------------|  
|状態|インデックスの状態。<br /><br /> **[保存]** をクリックしたときに表示される ![更新中状態のアイコン](../master-data-services/media/mds-statusicon-updating.png "更新中状態のアイコン") 画像は、インデックスが更新中であることを示します。<br /><br /> インデックスの作成中または編集中にエラーが発生すると、![エラー状態のアイコン](../master-data-services/media/mds-statusicon-error.png "エラー状態のアイコン") 画像が表示されます。<br /><br /> それ以外の場合は適切な状態であり、![適切な状態のアイコン](../master-data-services/media/mds-statusicon-ok.png "適切な状態のアイコン") 画像が表示されます。|  
|[オブジェクト名]|インデックス名。|  
|[Is Unique]|インデックスが一意かどうかを示します。|  
|[On Attributes] (属性)|インデックスが定義されている属性の表示名を示します。|  
  
 インデックスをクリックすると、次の情報が表示されます。  
  
-   **作成者**: インデックスを作成したユーザーの名前。  
  
-   **作成日時**: インデックスが作成された日時。  
  
-   **更新者**: インデックスを最後に更新したユーザーの名前。  
  
-   **更新日時**: インデックスが最後に更新された日時。  
  
## <a name="next-steps"></a>Next Steps  
 [インデックスの編集と削除 (マスター データ サービス)](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [カスタム インデックス (マスター データ サービス)](../master-data-services/custom-index-master-data-services.md)  
  
  
