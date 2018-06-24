---
title: 変更の追跡 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fb6760d737656b0c8fedb82b315d45e59152de79
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076003"
---
# <a name="change-tracking-master-data-services"></a>変更の追跡 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、変更の追跡グループを使用して、属性の値が変化したときにアクションを実行できます。 新しい値がどうなるかわからないけれども、変更が発生した場合にそれを知りたいときに、変更の追跡を使用します。  
  
## <a name="configuring-change-tracking"></a>変更の追跡を構成する  
 変更の追跡を構成するには、変更の追跡グループに属性を追加します。 グループは、1 つまたは複数の属性を含むことができます。 その後、ビジネス ルールを作成し、グループ内のいずれかの属性が変化したときに実行するアクションを定義します。  
  
> [!NOTE]  
>  変更の追跡のビジネス ルールでは、ステージング (インポートされた) データが変更されるものと想定します。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|変更の追跡グループに属性を追加します。|[変更の追跡グループに属性を追加&#40;マスター データ サービス&#41;](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|属性の変更に基づいてアクションを開始するビジネス ルールを作成します。|[属性値の変更に基づいてアクションを開始する&#40;マスター データ サービス&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [検証 (マスター データ サービス)](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [属性&#40;マスター データ サービス&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  