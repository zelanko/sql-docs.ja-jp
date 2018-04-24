---
title: コレクション アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 790d55f17db48b1d3b76b6cc920a4204099d48f1
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="collection-permissions-master-data-services"></a>コレクション権限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  コレクション権限は、エンティティのすべてのコレクションに適用されます。 特定のコレクションに権限を与えることはできません。つまり、権限はすべてのコレクションに適用されます。  
  
> [!NOTE]  
>  これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
|権限|Description|  
|----------------|-----------------|  
|**読み取り**|ユーザーがコレクションのメンバーとメンバーの属性を読み取ることができます。|  
|**作成**|ユーザーがコレクションのメンバーを作成して属性値を割り当てることができます。|  
|**Update**|ユーザーがコレクションのメンバー、属性、リレーションシップを更新できます。|  
|**削除**|ユーザーがコレクションのメンバーを削除できます。|  
|**Deny**|コレクション メンバーに対するアクセスをすべて拒否します。|  
  
 読み取り、作成、更新、削除の各権限は組み合わせることができます。 作成、更新、削除が割り当てられると、読み取り権限が自動的に割り当てられます。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
