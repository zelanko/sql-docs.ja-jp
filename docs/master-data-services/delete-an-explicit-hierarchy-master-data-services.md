---
title: 明示的階層を削除する
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d49665fff9fe5821bf5cb38e908202483f2250b5
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812386"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>明示的階層を削除する (マスター データ サービス)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になった明示的階層を削除します。  
  
> [!WARNING]  
>  明示的階層を削除すると、階層内の統合メンバーもすべて削除されます。 エンティティに対する明示的階層を削除すると、エンティティのコレクションもすべて削除され、明示的階層およびコレクションに対してエンティティが無効になります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-an-explicit-hierarchy"></a>明示的階層を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  [**モデルの管理**] ページで、グリッドからモデルを選択し、[**エンティティ**] をクリックします。  
  
3.  **[エンティティの管理]** ページで、削除する明示的階層を含むエンティティの行をグリッドから選択します。  
  
4.  [**明示的階層**] をクリックします。  
  
5.  **[明示的階層の管理]** ページで、削除する明示的階層をクリックします。  
  
6.  **[編集]** をクリックします。  
  
7.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [明示的階層 &#40;マスターデータサービスを作成し&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
