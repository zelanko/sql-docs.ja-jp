---
title: "エンティティの同期関係の編集と削除 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5e37f3-352e-45a6-b4a0-6f98f83b4bd8
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 68b60fa3d77ae5786419e83dbbdfc9967130cb59
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="edit-and-delete-an-entity-sync-relationship-master-data-services"></a>エンティティの同期関係の編集と削除 (マスター データ サービス)
  エンティティ同期は、エンティティのバージョン間での反復可能な一方向の同期です。 異なるモデルの間でエンティティ データを共有する方法を提供します。 自分で作成した同期関係は編集および削除できます。  
  
## <a name="prerequisites"></a>前提条件  
 エンティティの同期関係を編集するための前提条件を次に示します。  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   ターゲット モデルのモデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも、ソース エンティティとそのすべての属性およびメンバーに対する読み取りアクセス権が必要です。  
  
 エンティティの同期関係を削除するための前提条件を次に示します。  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   ターゲット モデルのモデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
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
  
1.  マスター データ マネージャーで、 **[システム管理]**をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして、 **[Entity Sync]**(エンティティの同期) をクリックします。  
  
3.  **[Entity Sync Maintenance]** (エンティティの同期のメンテナンス) ページで、グリッド内の同期関係を選択します。  
  
4.  **[編集]**をクリックします。 右側にパネルが表示されます。  
  
5.  **[頻度]**を変更します。 **[Sync On Demand]**(オンデマンドで同期) を選択するか、 **[Auto Sync]** (自動同期) を選択して頻度を設定します。  
  
6.  **[保存]**をクリックします。  
  
 **エンティティの同期関係を削除するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]**をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして、 **[Entity Sync]**(エンティティの同期) をクリックします。  
  
3.  **[Entity Sync Maintenance]** (エンティティの同期のメンテナンス) ページで、グリッド内の同期関係を選択します。  
  
4.  **[削除]**をクリックします。  
  
5.  確認ダイアログで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [エンティティの同期関係の作成と実行 (マスター データ サービス)](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [エンティティの同期関係 (マスター データ サービス)](../master-data-services/entity-sync-relationship-master-data-services.md)  
  
  

