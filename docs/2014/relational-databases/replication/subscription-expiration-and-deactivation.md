---
title: サブスクリプションの有効期限と非アクティブ化 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distributors [SQL Server replication], distribution retention period
- subscriptions [SQL Server replication], expiration
- publications [SQL Server replication], publication retention periods
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- publication retention periods
- distribution retention period
- subscriptions [SQL Server replication], deactivation
- deactivating subscriptions
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d81e8b5c02fcfe5399be9e63c8160036a999547
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997940"
---
# <a name="subscription-expiration-and-deactivation"></a>サブスクリプションの有効期限と非アクティブ化
  サブスクリプションは、指定した *保有期間*内に同期されなかった場合、非アクティブ化されるか、期限切れにされる可能性があります。 行われる処理は、レプリケーションの種類と保有期間が過ぎているかどうかによって異なります。  
  
 保有期間を設定する場合は、「[サブスクリプションの有効期限の設定](publish/set-the-expiration-period-for-subscriptions.md)」、「[トランザクション パブリケーションのディストリビューションの保有期間の設定 &#40;SQL Server Management Studio&#41;](set-distribution-retention-period-for-transactional-publications.md)」および「[パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)」を参照してください。  
  
## <a name="transactional-replication"></a>トランザクション レプリケーション  
 トランザクションレプリケーションでは、ディストリビューションの最大保有期間 ( **@max_distretention** [Sp_adddistributiondb &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)) とパブリケーションの保有期間 ( **@retention** [sp_addpublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)のパラメーター) を使用します。  
  
-   ディストリビューションの最大保有期間 (既定値は 72 時間) 内にサブスクリプションが同期されず、ディストリビューション データベース内にサブスクライバーに配信されていない変更がある場合、そのサブスクリプションは、ディストリビューターで実行される **ディストリビューションのクリーンアップ** ジョブによって非アクティブ化にマークされます。 サブスクリプションを再初期化する必要があります。  
  
-   パブリケーションの保有期間 (既定値は 336 時間) 内にサブスクリプションが同期されない場合は、サブスクリプションは期限切れとなり、パブリッシャーで実行される **有効期限が切れたサブスクリプションのクリーンアップ** ジョブによって削除されます。 サブスクリプションを再作成し、同期する必要があります。  
  
     プッシュ サブスクリプションの期限が切れた場合は完全に削除されますが、プル サブスクリプションの場合は削除されません。 プル サブスクリプションは、サブスクライバーでクリーンアップする必要があります。 詳細については、「 [Delete a Pull Subscription](delete-a-pull-subscription.md)」を参照してください。  
  
## <a name="merge-replication"></a>マージ レプリケーション  
 マージレプリケーションでは、パブリケーションの保有期間 **@retention** ( **@retention_period_unit** [sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)のパラメーターとパラメーター) を使用します。 サブスクリプションが期限切れになると、そのサブスクリプションのメタデータが削除されるため、サブスクリプションを再初期化する必要があります。 再初期化されていないサブスクリプションは、パブリッシャーで実行される、 **有効期限が切れたサブスクリプションのクリーンアップ** ジョブによって削除されます。 既定では、このジョブは毎日実行されます。このジョブにより、パブリケーションの保有期間の 2 倍の期間にわたって同期されなかったすべてのプッシュ サブスクリプションが削除されます。 次に例を示します。  
  
-   パブリケーションの保有期間が 14 日間である場合、サブスクリプションは 14 日以内に同期されなかった場合に期限切れになる可能性があります。  
  
     パブリッシャーが [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンを実行しており、サブスクリプションのエージェントが [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンから実行されている場合は、サブスクリプションのパーティション内のデータに変更があった場合にのみ、サブスクリプションは期限切れになります。 たとえば、サブスクライバーが、ドイツの顧客に関する顧客データのみを受信するとします。 保有期間が 14 日間に設定されているとすると、最近 14 日間でドイツの顧客データに変更があった場合にのみ、このサブスクリプションは 14 日目に期限切れになります。  
  
-   最後の同期からの経過日数が 14 日から 27 日の間は、サブスクリプションを再初期化できます。  
  
-   最後の同期後 28 日目に、サブスクリプションは、 **有効期限が切れたサブスクリプションのクリーンアップ** ジョブによって削除されます。 プッシュ サブスクリプションの期限が切れた場合は完全に削除されますが、プル サブスクリプションの場合は削除されません。 プル サブスクリプションは、サブスクライバーでクリーンアップする必要があります。 詳細については、「 [Delete a Pull Subscription](delete-a-pull-subscription.md)」を参照してください。  
  
### <a name="considerations-for-setting-the-publication-retention-period-for-merge-publications"></a>マージ パブリケーションに対するパブリケーション保有期間の設定に関する注意点  
 マージ パブリケーションの保有期間を設定する場合は、以下の点に注意してください。  
  
-   マージ パブリケーションの保有期間には、異なるタイム ゾーンのサブスクライバーに対応するため、24 時間の猶予期間があります。 たとえば、保有期間を 1 日に設定した場合、実際の保有期間は 48 時間となります。  
  
-   マージ レプリケーション メタデータのクリーンアップは、パブリケーション保有期間に依存します。  
  
    -   保有期間が終了するまで、パブリケーションおよびサブスクリプション データベースでメタデータをクリーンアップすることはできません。 レプリケーション パフォーマンスを低下させる可能性があるため、保有期間に大きな値を指定する際は注意してください。 すべてのサブスクライバーが保有期間内で定期的に同期されることを確実に予測できる場合は、小さい値を使用することをお勧めします。  
  
    -   サブスクリプションが期限切れにならないように指定することができます (の値は 0 **@retention** )。ただし、メタデータをクリーンアップできないため、この値は使用しないことを強くお勧めします。  
  
-   リパブリッシャーの保有期間は、元のパブリッシャーで設定されている保有期間以下の値に設定する必要があります。 また、すべてのパブリッシャーとその代替同期パートナーに対するパブリケーションの保有期間の値は、同じにする必要があります。 異なる値を使用すると、集約されなくなる可能性があります。 パブリケーションの保有期間の値を変更する必要がある場合は、サブスクライバーを再初期化して、データの未集約が発生しないようにします。  
  
-   クリーンアップ後、パブリケーションの保有期間を延長し、既にメタデータを削除したパブリッシャーとのマージをサブスクリプションが試行した場合、保有期間の値が増加しているため、そのサブスクリプションは期限切れになりません。 ただし、パブリッシャーには、サブスクライバーに変更をダウンロードするための十分なメタデータが存在しないため、未集約が発生します。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの再初期化](reinitialize-subscriptions.md)   
 [レプリケーション エージェントの管理](agents/replication-agent-administration.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
