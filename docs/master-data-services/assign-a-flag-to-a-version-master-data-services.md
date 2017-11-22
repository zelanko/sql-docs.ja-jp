---
title: "バージョンにフラグを割り当てる (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de71fb691aeebe07cd952097033415a94e46ee82
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a>バージョンにフラグを割り当てる (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、バージョンにフラグを割り当てて、ユーザーまたはサブスクライブ システムが使用する必要があるバージョンを示します。  
  
> [!NOTE]  
>  バージョン フラグは一度に 1 つのバージョンにしか割り当てることができません。 別のバージョンに既に割り当てられているフラグを割り当てた場合、フラグは、選択したバージョンに移動します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   割り当てるバージョン フラグを作成している必要があります。 詳細については、「 [バージョン フラグを作成する (マスター データ サービス)](../master-data-services/create-a-version-flag-master-data-services.md)」を参照してください。  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
### <a name="to-assign-a-flag-to-a-version"></a>フラグをバージョンに割り当てるには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]**をクリックします。  
  
2.  **[バージョンの管理]** ページで、フラグを割り当てるバージョンの行の **[フラグ]** 列のセルをダブルクリックします。  
  
3.  一覧から、割り当てるフラグを選択します。  
  
    > [!NOTE]  
    >  フラグが使用できない場合、そのフラグは **[コミット済み]** のバージョンのみで使用できる可能性があります。 これを確認するには、 **[バージョン フラグの管理]** ページに移動し **[コミット済みのバージョンのみ]** フィールドでそのフラグを確認します。  
  
4.  Enter キーを押して変更を保存します。  
  
## <a name="see-also"></a>参照  
 [バージョン フラグを作成する (マスター データ サービス)](../master-data-services/create-a-version-flag-master-data-services.md)   
 [バージョン (マスター データ サービス)](../master-data-services/versions-master-data-services.md)  
  
  
