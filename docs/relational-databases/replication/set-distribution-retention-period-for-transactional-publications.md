---
title: トランザクション パブリケーションのディストリビューションの保有期間の設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7ba35c0cdc52557b179beaec259fd4c5d7f5d698
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514685"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>トランザクション パブリケーションのディストリビューションの保有期間の設定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[ディストリビューション データベースのプロパティ - \<DistributionDatabase>]** ダイアログ ボックスで、ディストリビューションの最小保有期間と最大保有期間を指定します。 このダイアログ ボックスは、**[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページから使用できます。 このダイアログ ボックスへのアクセスの詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
### <a name="to-specify-the-distribution-retention-period"></a>ディストリビューションの保有期間を指定するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページで、ディストリビューション データベースのプロパティ ボタン (**[...]**) をクリックします。  
  
2.  ディストリビューションの最小保有期間を指定するには **[最小]** ボックスに値を入力し、ディストリビューションの最大保有期間を指定するには **[最大]** ボックスに値を入力します。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)   
 [サブスクリプションの有効期限と非アクティブ化](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
