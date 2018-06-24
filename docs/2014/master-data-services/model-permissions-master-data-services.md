---
title: モデル アクセス許可 (Master Data Services) | Microsoft Docs
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
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e92f595bcf701e20378fe94dfde6c91d8c57bee1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074405"
---
# <a name="model-permissions-master-data-services"></a>モデル権限 (Master Data Services)
  モデル権限は、モデル内に存在するすべてのエンティティ、派生階層、明示的階層、およびコレクションに適用されます。 モデルに割り当てられる権限は、個々のオブジェクトでオーバーライドすることができます。  
  
> [!NOTE]  
>  ユーザーがモデル管理者の場合、そのモデルはユーザー インターフェイスのすべての機能領域に表示されます。 それ以外の場合、モデルは **[エクスプローラー]** 機能領域にのみ表示されます。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用です。**|**エクスプ ローラー**モデルが表示されますが、ユーザーを追加できません、またはメンバーの削除、および属性値、階層メンバーシップ、またはコレクション メンバーシップを更新することはできません。|  
|**Update**|**エクスプ ローラー**にモデルが表示され、ユーザーを追加したり、メンバーを削除する属性値、階層メンバーシップ、およびコレクションのメンバーシップを更新します。|  
|**Deny**|モデルが表示されません。|  
  
 モデルに権限を割り当てると、ユーザーはすべてのバージョンのモデルにアクセスできるようになります。 個々のバージョンに権限を割り当てることはできません。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる&#40;マスター データ サービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル オブジェクト権限&#40;マスター データ サービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [エンティティ アクセス許可 (マスター データ サービス)](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [コレクション アクセス許可 (マスター データ サービス)](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  