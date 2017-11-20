---
title: "変更の追跡 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/15/2017
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
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 0def93a0f88d19ba894508d4a5d39de59dbd7a28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="change-tracking-master-data-services"></a>変更の追跡 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、変更の追跡グループを使用して、属性の値が変化したときにアクションを実行できます。 新しい値がどうなるかわからないけれども、変更が発生した場合にそれを知りたいときに、変更の追跡を使用します。  
  
## <a name="configuring-change-tracking"></a>変更の追跡を構成する  
 変更の追跡を構成するには、変更の追跡グループに属性を追加します。 グループは、1 つまたは複数の属性を含むことができます。 その後、ビジネス ルールを作成し、グループ内のいずれかの属性が変化したときに実行するアクションを定義します。  
  
> [!NOTE]  
>  変更の追跡のビジネス ルールでは、ステージング (インポートされた) データが変更されるものと想定します。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|変更の追跡グループに属性を追加します。|[変更の追跡グループに属性を追加する (マスター データ サービス)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|属性の変更に基づいてアクションを開始するビジネス ルールを作成します。|[属性値の変更に基づいてアクションを開始する (マスター データ サービス)](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [検証 (マスター データ サービス)](../master-data-services/validation-master-data-services.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
-   [属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)  
  
  

