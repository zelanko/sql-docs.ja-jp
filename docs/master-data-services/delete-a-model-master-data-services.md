---
title: モデルを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting models [Master Data Services]
- models [Master Data Services], deleting models
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 23c5697b863646bac824b196696345566c06a747
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906448"
---
# <a name="delete-a-model-master-data-services"></a>モデルを削除する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  モデルを削除して、モデルおよびそのすべてのデータを [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]から削除します。  
  
> [!NOTE]  
>  これらの手順が完了すると、モデルのすべてのバージョンのすべてのオブジェクトおよびすべてのデータが完全に削除されます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 &#40;マスター データ サービス&#41;](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-delete-a-model"></a>モデルを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[モデル]** をクリックします。  
  
3.  **[モデルの管理]** ページで、グリッドから削除するモデルの行を選択します。  
  
4.  **[削除]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
6.  追加の確認のダイアログ ボックスで **[OK]** をクリックします。  
  
 グリッドの **[状態]** 列には、モデルに対する操作の状態が示されます。 **[モデルの保存]** ボタンをクリックすると、モデルが更新されていることを示す ![更新中](../master-data-services/media/mds-model-status-updating.png "更新中") 画像が表示されます。 モデルの作成中または編集中にエラーが発生すると、![エラー](../master-data-services/media/mds-model-status-error.png "エラー") 画像が表示されます。 それ以外の場合は正常な状態であり、 ![[OK]](../master-data-services/media/mds-model-status-ok.png "[OK]") 画像が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [モデル (マスター データ サービス)](../master-data-services/models-master-data-services.md)   
 [モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)  
  
  
