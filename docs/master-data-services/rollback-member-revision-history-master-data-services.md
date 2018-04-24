---
title: メンバー リビジョン履歴のロールバック (マスター データ サービス) | Microsoft Docs
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
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b4291383c9f2f1d41ea13997f2feeb6e7c1014d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="rollback-member-revision-history-master-data-services"></a>メンバー リビジョン履歴のロールバック (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  メンバー リビジョン履歴は、メンバーが変更されるたびに記録されます。 メンバー リビジョン履歴は前のバージョンにロールバックすることができます。  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   選択したメンバーの少なくとも 1 つの属性を更新できるアクセス許可が必要です。 リビジョン履歴をロールバックすると、更新できるすべての属性値が前のバージョンの値にロールバックされます。  
  
-   リビジョン履歴は、エンティティのトランザクション ログの種類がメンバーである場合にのみ使用できます。  
  
 **メンバー リビジョン履歴をロールバックするには**  
  
1.  マスター データ マネージャーで、[エクスプローラー] をクリックします。  
  
2.  ロールバックするエンティティとメンバーを選択します。  
  
3.  **[履歴の表示]** をクリックします。  
  
4.  ロールバックするリビジョンを選択し、 **[ロールバック]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [メンバー リビジョン履歴 (マスター データ サービス)](../master-data-services/member-revision-history-master-data-services.md)   
 [エンティティのトランザクション ログの種類の変更 (マスター データ サービス)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
