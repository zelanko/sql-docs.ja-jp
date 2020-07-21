---
title: バージョンにフラグを割り当てる (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 94c387915d4962eba4d97aa758ca5d5a2aa74b13
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972242"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a>バージョンにフラグを割り当てる (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、バージョンにフラグを割り当てて、ユーザーまたはサブスクライブ システムが使用する必要があるバージョンを示します。  
  
> [!NOTE]  
>  バージョン フラグは一度に 1 つのバージョンにしか割り当てることができません。 別のバージョンに既に割り当てられているフラグを割り当てた場合、フラグは、選択したバージョンに移動します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   割り当てるバージョン フラグを作成している必要があります。 詳細については、「 [バージョン フラグを作成する (マスター データ サービス)](../../2014/master-data-services/create-a-version-flag-master-data-services.md)」を参照してください。  
  
### <a name="to-assign-a-flag-to-a-version"></a>フラグをバージョンに割り当てるには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  **[バージョンの管理]** ページで、フラグを割り当てるバージョンの行の **[フラグ]** 列のセルをダブルクリックします。  
  
3.  一覧から、割り当てるフラグを選択します。  
  
    > [!NOTE]  
    >  フラグが使用できない場合、そのフラグは **[コミット済み]** のバージョンのみで使用できる可能性があります。 これを確認するには、 **[バージョン フラグの管理]** ページに移動し **[コミット済みのバージョンのみ]** フィールドでそのフラグを確認します。  
  
4.  Enter キーを押して変更を保存します。  
  
## <a name="see-also"></a>参照  
 [バージョンフラグ &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)   
 [バージョン (マスター データ サービス)](../../2014/master-data-services/versions-master-data-services.md)  
  
  
