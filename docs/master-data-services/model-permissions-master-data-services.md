---
title: モデル アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d64737f0da6faabb2be218da19f2c04b4591d681
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35330206"
---
# <a name="model-permissions-master-data-services"></a>モデル権限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  モデル権限は、モデル内に存在するすべてのエンティティ、派生階層、明示的階層、およびコレクションに適用されます。 モデルに割り当てられる権限は、個々のオブジェクトでオーバーライドすることができます。  
  
> [!NOTE]  
>  ユーザーがモデル管理者の場合、そのモデルはユーザー インターフェイスのすべての機能領域に表示されます。 それ以外の場合、モデルは **[エクスプローラー]** 機能領域にのみ表示されます。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
|権限|[説明]|  
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
  
  
