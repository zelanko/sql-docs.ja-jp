---
title: "インデックス (マスター データ サービス) を作成 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a4d03606ab8a45d6c7b326fd64b6900ac7e67356
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-an-index-master-data-services"></a>インデックスを作成する (マスター データ サービス)
  頻繁にクエリを実行する属性の一覧にカスタム インデックスを作成して、クエリのパフォーマンスを高めます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
 **インデックスを作成するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]**をクリックします。  
  
2.  **[Manage Model]** (モデルの管理) ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、インデックスを作成するエンティティの行を **グリッド** から選択します。  
  
4.  **[インデックス]**をクリックします。  
  
5.  **[名前]** ボックスに、このインデックスの名前を入力します。  
  
6.  一意なインデックスを作成する場合は、 **[Is Unique]** (一意) を選択します。 インデックスの種類の詳細については、「 [カスタム インデックス (マスター データ サービス)](../master-data-services/custom-index-master-data-services.md)」を参照してください。  
  
7.  **[使用できる属性]** ボックスの属性をクリックし、 **[追加]** 矢印をクリックします。 すべての属性を追加するには、 **[すべて追加]** 矢印をクリックします。  
  
8.  **[保存]**をクリックします。  
  
 作成されたインデックスごとに、4 列の行がグリッドに追加されます。 次の表で各列について説明します。  
  
|列名|Description|  
|-----------------|-----------------|  
|[状態]|インデックスの状態。<br /><br /> クリックすると、**保存**、![ステータスの更新のアイコン](../master-data-services/media/mds-statusicon-updating.png "ステータスの更新のアイコン")インデックスが更新されていることを示すイメージが表示されます。<br /><br /> 作成またはインデックスを編集するときにエラーがある場合、![のエラー状態をアイコン](../master-data-services/media/mds-statusicon-error.png "のエラー状態をアイコン")イメージが表示されます。<br /><br /> それ以外の場合、適切な状態で、および![OK ステータス アイコン](../master-data-services/media/mds-statusicon-ok.png "OK ステータス アイコン")イメージが表示されます。|  
|名前|インデックス名。|  
|[Is Unique]|インデックスが一意かどうかを示します。|  
|[On Attributes] (属性)|インデックスが定義されている属性の表示名を示します。|  
  
 インデックスをクリックすると、次の情報が表示されます。  
  
-   **作成者**: インデックスを作成したユーザーの名前。  
  
-   **作成日時**: インデックスが作成された日時。  
  
-   **更新者**: インデックスを最後に更新したユーザーの名前。  
  
-   **更新日時**: インデックスが最後に更新された日時。  
  
## <a name="next-steps"></a>次の手順  
 [インデックスの編集と削除 (マスター データ サービス)](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [カスタム インデックス (マスター データ サービス)](../master-data-services/custom-index-master-data-services.md)  
  
  
