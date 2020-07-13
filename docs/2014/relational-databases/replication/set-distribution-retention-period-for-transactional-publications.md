---
title: トランザクションパブリケーションのディストリビューション保有期間を設定する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a68f092c63e75196ab82a81d2a8ca36d13142813
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055666"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a>トランザクション パブリケーションのディストリビューションの保有期間の設定 (SQL Server Management Studio)
  [**ディストリビューションデータベースのプロパティ- \<DistributionDatabase> ** ] ダイアログボックスで、ディストリビューションの最小保有期間と最大保有期間を指定します。 これは、[**ディストリビューターのプロパティ \<Distributor> -** ] ダイアログボックスの **[全般**] ページで使用できます。 このダイアログ ボックスへのアクセスの詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
### <a name="to-specify-the-distribution-retention-period"></a>ディストリビューションの保有期間を指定するには  
  
1.  [**ディストリビューターのプロパティ- \<Distributor> ** ] ダイアログボックスの **[全般**] ページで、ディストリビューションデータベースのプロパティボタン ([.**..**]) をクリックします。  
  
2.  ディストリビューションの最小保有期間を指定するには **[最小]** ボックスに値を入力し、ディストリビューションの最大保有期間を指定するには **[最大]** ボックスに値を入力します。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [ディストリビューションの構成](configure-distribution.md)   
 [サブスクリプションの有効期限と非アクティブ化](subscription-expiration-and-deactivation.md)  
  
  
