---
title: "バージョンをロックする (マスター データ サービス) |Microsoft ドキュメント"
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
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8edd7ce020ad20917c4bdc76c636b8cf7a06fadd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="lock-a-version-master-data-services"></a>バージョンをロックする (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをロックして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。  
  
> [!NOTE]  
>  バージョンをロックしても、スーパー ユーザーおよびモデル管理者は、引き続きメンバーの追加、編集、および削除を行うことができます。 モデルに対する権限を持つその他のユーザーは、メンバーの表示のみを行うことができます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   バージョンのステータスは、**[未処理]** である必要があります。  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
### <a name="to-lock-a-version"></a>バージョンをロックするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]**をクリックします。  
  
2.  **[バージョンの管理]** ページで、ロックするバージョンの行を選択します。  
  
3.  **[ロック]**をクリックします。  
  
4.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [ビジネス ルール &#40; に対してバージョンを検証します。マスター データ サービス &#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [コミット済み & #40 です。マスター データ サービス &#41;](../master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [バージョンと #40 です。マスター データ サービス &#41;](../master-data-services/versions-master-data-services.md)   
 [バージョン &#40; をロック解除します。マスター データ サービス &#41;](../master-data-services/unlock-a-version-master-data-services.md)  
  
  
