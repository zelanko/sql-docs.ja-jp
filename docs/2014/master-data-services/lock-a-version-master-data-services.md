---
title: バージョンをロックする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bd611f0593aa1a99e075e3ea6cd506c48f705513
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302382"
---
# <a name="lock-a-version-master-data-services"></a>バージョンをロックする (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをロックして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。  
  
> [!NOTE]  
>  バージョンをロックしても、モデル管理者は、引き続きメンバーの追加、編集、および削除を行うことができます。 モデルに対する権限を持つその他のユーザーは、メンバーの表示のみを行うことができます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
-   バージョンのステータスは、**[未処理]** である必要があります。  
  
### <a name="to-lock-a-version"></a>バージョンをロックするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  **[バージョンの管理]** ページで、ロックするバージョンの行を選択します。  
  
3.  **[ロック]** をクリックします。  
  
4.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [ビジネス ルールに対してバージョンを検証&#40;マスター データ サービス&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [バージョンをコミットする&#40;マスター データ サービス&#41;](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [バージョン&#40;マスター データ サービス&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [バージョンをロック解除&#40;マスター データ サービス&#41;](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
