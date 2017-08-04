---
title: "バージョンをコミットする (マスター データ サービス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 28fd453f17c08b708b4a49f1f4646eb1be7a51ab
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="commit-a-version-master-data-services"></a>バージョンをコミットする (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] でモデルのバージョンをコミットして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。 コミットしたバージョンはロック解除できません。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   バージョンのステータスは、**[ロック済み]** である必要があります。 詳細については、「[バージョンをロックする (マスター データ サービス)](../master-data-services/lock-a-version-master-data-services.md)」を参照してください。  
  
-   すべてのメンバーが正常に検証されている必要があります。  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
### <a name="to-commit-a-version"></a>バージョンをコミットするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]**をクリックします。  
  
2.  **[バージョンの管理]** ページのメニュー バーの **[バージョンの検証]**をクリックします。  
  
3.  **[バージョンの検証]** ページで、コミットするモデルおよびバージョンを選択します。  
  
4.  **[コミット]**をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [バージョン フラグ &#40; を作成します。マスター データ サービス &#41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [バージョン &#40; にフラグを割り当てるマスター データ サービス &#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [バージョン &#40; をコピーします。マスター データ サービス &#41;](../master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [バージョンと #40 です。マスター データ サービス &#41;](../master-data-services/versions-master-data-services.md)  
  
  
