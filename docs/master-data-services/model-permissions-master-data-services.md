---
title: "モデル アクセス許可 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
caps.latest.revision: "6"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2f742b5222054c918dc37ceb609dbee525cc4521
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="model-permissions-master-data-services"></a>モデル権限 (Master Data Services)
  モデル権限は、モデル内に存在するすべてのエンティティ、派生階層、明示的階層、およびコレクションに適用されます。 モデルに割り当てられる権限は、個々のオブジェクトで無効にすることができます。  
  
> [!NOTE]  
>  ユーザーがモデル管理者の場合、そのモデルはユーザー インターフェイスのすべての機能領域に表示されます。 それ以外の場合、モデルは **[エクスプローラー]** 機能領域にのみ表示されます。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
|権限|Description|  
|----------------|-----------------|  
|**読み取り**|ユーザーは、メンバー、属性、階層メンバーシップ、コレクション メンバーシップを読み取ることができます。|  
|**作成**|ユーザーはメンバーを作成し、作成時に属性値を割り当てることができます。|  
|**Update**|ユーザーは、メンバー、属性、階層メンバーシップ、コレクション メンバーシップを更新できます。|  
|**削除**|ユーザーはメンバーを削除できます。|  
|**Deny**|モデルに対するすべてのアクセスを拒否します。|  
|**管理**|モデルに対する管理者権限です。 管理者権限はモデル レベルでのみ使用可能です。|  
  
 読み取り、作成、更新、削除の各権限は組み合わせることができます。 作成、更新、削除の各権限を割り当てた場合は、読み取り権限が自動的に割り当てられます。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)   
 [エンティティ アクセス許可 (マスター データ サービス)](../master-data-services/entity-permissions-master-data-services.md)   
 [コレクション アクセス許可 (マスター データ サービス)](../master-data-services/collection-permissions-master-data-services.md)  
  
  
