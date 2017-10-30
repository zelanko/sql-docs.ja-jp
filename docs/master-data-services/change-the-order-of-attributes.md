---
title: "属性の順序の変更 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 835a032c-e37c-4f35-8ab0-5e4ae25c2e9b
caps.latest.revision: 5
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 706bb911a55ff319cf8fdceb9ac31fed419ef960
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="change-the-order-of-attributes"></a>属性の順序の変更
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、属性の順序を変更できます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-change-the-order-of-an-attribute"></a>属性の順序を変更するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[エンティティの管理]** ページで、属性を作成するエンティティの行を選択します。  
  
4.  **[属性]**をクリックします。  
  
5.  **[属性の管理]** ページで、次のいずれかの操作を行います。  
  
    -   属性の対象がリーフ メンバーの場合、 **[メンバーの種類]** ボックスの一覧から **[リーフ]** を選択します。  
  
    -   属性の対象が統合メンバーの場合、 **[メンバーの種類]** ボックスの一覧から **[統合]** を選択します。  
  
    -   属性の対象がコレクションの場合、 **[メンバーの種類]** ボックスの一覧から **[コレクション]** を選択します。  
  
6.  順序を変更する属性の行を選択します。  
  
    > [!NOTE]  
    >  Name 属性または Code 属性の順序は変更できません。  
  
7.  **[上へ移動]** または **[下へ移動]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)  
  
  

