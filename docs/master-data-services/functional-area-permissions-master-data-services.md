---
title: 機能領域権限
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- functional area permissions [Master Data Services], about functional area permissions
- functional area permissions [Master Data Services]
- permissions [Master Data Services], functional areas
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4a76feabce6834ba260980044772e2ee53b953d
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811757"
---
# <a name="functional-area-permissions-master-data-services"></a>機能領域権限 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー インターフェイス (UI) の各機能領域に、権限を割り当てることができます。 機能領域を次に示します。  
  
-   **フローラ**  
  
-   **バージョン管理**  
  
-   **統合管理**  
  
-   **システム管理**  
  
-   **ユーザー/グループの権限**  
  
-   **スーパー ユーザー**  
  
 機能領域に権限を割り当てると、UI のその領域がユーザーまたはグループに表示されます。  
  
 **[エクスプローラー]** 機能領域内でユーザーがアクセスできるデータは、モデル オブジェクトおよび階層メンバーに割り当てられた追加権限によって決定されます。 その他のすべての機能領域内でモデルを表示および操作するには、ユーザーはモデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
> [!IMPORTANT]  
>  スーパー ユーザー権限を持つユーザーは、実質的にすべてのモデルに対する管理者権限を持ち、その他のすべての機能権限を持ちます。  
  
 **にアクセスするには、ユーザーまたはグループが、少なくとも 1 つの機能領域および** [モデル] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]タブに表示される少なくとも 1 つのモデルに対する権限を持っている必要があります。  
  
## <a name="see-also"></a>関連項目  
 [機能領域のアクセス許可を割り当て &#40;マスターデータサービス&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [階層メンバーの権限 &#40;マスターデータサービス&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [権限の決定方法 (マスター データ サービス)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
