---
title: "Code 属性の値の自動生成 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 77518517fd1ea62753282d368fb41d785445011d
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Code 属性の値の自動生成 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、新しいメンバーが作成されるたびにエンティティの Code 属性の値に整数を自動的に割り当てる場合は、Code 属性の値を自動的に生成します。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   エンティティが存在する必要があります。 詳細については、「[エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)」を参照してください。  
  
### <a name="to-automatically-generate-code-values"></a>コード値を自動的に生成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページで、編集するエンティティが含まれているモデルの行を選択し、 **[エンティティ]**をクリックします。  
  
3.  **[エンティティの管理]** ページで、コードを生成するエンティティの行を選択し、 **[編集]**をクリックします。  
  
4.  **[コード値を自動的に作成する]** チェック ボックスをオンにします。  
  
5.  **[開始]** ボックスに、増分を開始する値を入力します。 メンバーが既に存在する場合は、コードは既存の最も大きい値に基づいて設定されます。 たとえば、最も大きい既存のコード値が 299 の場合、次のメンバーのコード値は 300 に設定されます。  
  
6.  **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [コードの自動作成 (マスター データ サービス)](../master-data-services/automatic-code-creation-master-data-services.md)   
 [Code 以外の属性の値の自動生成 (マスター データ サービス)](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
