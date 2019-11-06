---
title: エンティティの同期関係の編集と削除 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9a5e37f3-352e-45a6-b4a0-6f98f83b4bd8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 52ffe540d1afe9334533c2a5a8a631f342aed983
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086459"
---
# <a name="edit-and-delete-an-entity-sync-relationship-master-data-services"></a>エンティティの同期関係の編集と削除 (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  エンティティ同期は、エンティティのバージョン間での反復可能な一方向の同期です。 異なるモデルの間でエンティティ データを共有する方法を提供します。 自分で作成した同期関係は編集および削除できます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 エンティティの同期関係を編集するための前提条件を次に示します。  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   ターゲット モデルのモデル管理者である必要があります。 詳細については、「 [管理者 &#40;マスター データ サービス&#41;](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   少なくとも、ソース エンティティとそのすべての属性およびメンバーに対する読み取りアクセス権が必要です。  
  
 エンティティの同期関係を削除するための前提条件を次に示します。  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   ターゲット モデルのモデル管理者である必要があります。 詳細については、「 [管理者 &#40;マスター データ サービス&#41;](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
 エンティティの同期関係を編集する際には、次の点に注意してください。  
  
-   ソース エンティティとターゲット エンティティは、異なるモデルに存在する必要があります。  
  
-   ターゲット エンティティのバージョンの状態をコミットすることはできません。  
  
-   同期関係が確立されると、ターゲットはすぐにソースと同期します。  
  
-   ターゲット エンティティのバージョンを、別の同期関係のソース エンティティのバージョンにすることはできません。  
  
 エンティティの同期関係を実行する際には、次の点に注意してください。  
  
-   リーフ メンバーのみがコピーされます。  
  
-   ドメイン ベースの属性はコピーされません。  
  
-   論理削除されたメンバーはコピーされません。  
  
-   同期では、ターゲット エンティティのトランザクション/履歴は生成されません。  
  
 **エンティティの同期関係を編集するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして、 **[Entity Sync]** (エンティティの同期) をクリックします。  
  
3.  **[Entity Sync Maintenance]** (エンティティの同期のメンテナンス) ページで、グリッド内の同期関係を選択します。  
  
4.  **[編集]** をクリックします。 右側にパネルが表示されます。  
  
5.  **[頻度]** を変更します。 **[Sync On Demand]** (オンデマンドで同期) を選択するか、 **[Auto Sync]** (自動同期) を選択して頻度を設定します。  
  
6.  **[保存]** をクリックします。  
  
 **エンティティの同期関係を削除するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして、 **[Entity Sync]** (エンティティの同期) をクリックします。  
  
3.  **[Entity Sync Maintenance]** (エンティティの同期のメンテナンス) ページで、グリッド内の同期関係を選択します。  
  
4.  **[削除]** をクリックします。  
  
5.  確認ダイアログで **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [エンティティの同期関係の作成と実行 (マスター データ サービス)](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [エンティティの同期関係 (マスター データ サービス)](../master-data-services/entity-sync-relationship-master-data-services.md)  
  
  
