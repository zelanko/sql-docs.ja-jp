---
title: グループを追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b27e8fc54866d1311c98444becefddbe8697fbf
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-group-master-data-services"></a>グループを追加する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  **で** [グループ] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ボックスの一覧にグループを追加して、Web アプリケーションに権限を割り当てるプロセスを開始します。 グループ内のユーザーが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスできるようにするには、グループの権限を 1 つまたは複数の機能領域およびモデル オブジェクトに付与する必要があります。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
### <a name="to-add-a-group"></a>グループを追加するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。  
  
2.  **[ユーザー]** ページでメニュー バーから **[グループの管理]** をクリックします。  
  
3.  **[グループの追加]** をクリックします。  
  
4.  グループの名前を Active Directory ドメイン名またはサーバー コンピューターの名前の後に入力します ( *domain\group_name* または *computer\group_name*のように入力します)。  
  
5.  必要に応じて、 **[名前の確認]** をクリックします。  
  
6.  **[OK]** をクリックします。  
  
    > [!NOTE]  
    >  ユーザーが最初に [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスしたときに、そのユーザーの名前が [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー一覧に追加されます。  
  
## <a name="next-steps"></a>Next Steps  
  
-   [機能領域の権限を割り当てる (マスター データ サービス)](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [セキュリティ (マスター データ サービス)](../master-data-services/security-master-data-services.md)  
  
  
