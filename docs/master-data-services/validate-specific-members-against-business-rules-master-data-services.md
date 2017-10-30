---
title: "ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 293a1a5f1614df67cd1a28d88a432cc55a3927b7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールに対してメンバーのサブセットを更新または検証する場合にビジネス ルールを選択的に適用します。  
  
> [!NOTE]  
>  ビジネス ルールをモデルのバージョンのすべてのメンバーに適用する場合は、「 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   ビジネス ルールを適用するモデル オブジェクトに対して、 **更新** 権限が最低限必要です。  
  
### <a name="to-apply-business-rules-selectively"></a>ビジネス ルールを選択的に適用するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ドロップダウン リストからモデルを選択します。  
  
2.  **[バージョン]** ドロップダウン リストからバージョンを選択します。  
  
3.  **[エクスプローラー]** タブをクリックします。  
  
4.  メニュー バーの **[エンティティ]** をポイントして、ルールを適用するメンバーを含むエンティティの名前をクリックします。  
  
5.  **[ルールの適用]**をクリックします。 ビジネス ルールは、グリッドに表示されているメンバーにのみ適用されます。  
  
## <a name="see-also"></a>参照  
 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
  

