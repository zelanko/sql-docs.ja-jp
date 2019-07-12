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
ms.openlocfilehash: f352a52905e4f67760e7e6c4e9f46c08fdbdd5a9
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583757"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>トランザクション パブリケーションのディストリビューションの保有期間の設定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[ディストリビューション データベースのプロパティ - \<DistributionDatabase>]** ダイアログ ボックスで、ディストリビューションの最小保有期間と最大保有期間を指定します。 このダイアログ ボックスは、 **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページから使用できます。 このダイアログ ボックスへのアクセスの詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
### <a name="to-specify-the-distribution-retention-period"></a>ディストリビューションの保有期間を指定するには  
  
1.  **[ディストリビューターのプロパティ - \<ディストリビューター>]** ダイアログ ボックスの **[全般]** ページで、ディストリビューション データベースのプロパティ ボタン ( **[?]** ) をクリックします。  
  
2.  ディストリビューションの最小保有期間を指定するには **[最小]** ボックスに値を入力し、ディストリビューションの最大保有期間を指定するには **[最大]** ボックスに値を入力します。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)   
 [サブスクリプションの有効期限と非アクティブ化](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
