---
title: モデル アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971182"
---
# <a name="model-permissions-master-data-services"></a>モデル権限 (Master Data Services)
  モデル権限は、モデル内に存在するすべてのエンティティ、派生階層、明示的階層、およびコレクションに適用されます。 モデルに割り当てられる権限は、個々のオブジェクトでオーバーライドすることができます。  
  
> [!NOTE]  
>  ユーザーがモデル管理者の場合、そのモデルはユーザー インターフェイスのすべての機能領域に表示されます。 それ以外の場合、モデルは **[エクスプローラー]** 機能領域にのみ表示されます。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用**|[**エクスプローラー**] にモデルが表示されますが、ユーザーはメンバーを追加または削除できません。また、属性値、階層メンバーシップ、コレクションメンバーシップを更新することもできません。|  
|**Update**|[**エクスプローラー**] にモデルが表示され、ユーザーはメンバーを追加および削除したり、属性値、階層メンバーシップ、コレクションメンバーシップを更新したりできます。|  
|**Deny**|モデルが表示されません。|  
  
 モデルに権限を割り当てると、ユーザーはすべてのバージョンのモデルにアクセスできるようになります。 個々のバージョンに権限を割り当てることはできません。  
  
## <a name="see-also"></a>参照  
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [エンティティのアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [コレクション アクセス許可 (マスター データ サービス)](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
