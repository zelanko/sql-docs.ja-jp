---
title: "変更の追跡 (マスター データ サービス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6851da978ab681f0236bc9737e7f628c0089abe0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

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
|変更の追跡グループに属性を追加します。|[変更の追跡グループ &#40; に属性を追加します。マスター データ サービス &#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|属性の変更に基づいてアクションを開始するビジネス ルールを作成します。|[属性値の変更 &#40; に基づいてアクションを開始します。マスター データ サービス &#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [検証と #40 です。マスター データ サービス &#41;](../master-data-services/validation-master-data-services.md)  
  
-   [ビジネス ルール & #40 です。マスター データ サービス &#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [属性と #40 です。マスター データ サービス &#41;](../master-data-services/attributes-master-data-services.md)  
  
  
