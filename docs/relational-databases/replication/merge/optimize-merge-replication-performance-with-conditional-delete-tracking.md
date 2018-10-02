---
title: 条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
- articles [SQL Server replication], conditional delete tracking
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a326feef177287953982c94412d9619c716e2e22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692950"
---
# <a name="optimize-merge-replication-performance-with-conditional-delete-tracking"></a>条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 マージ レプリケーションでは、1 つ以上のアーティクルに対する削除が、レプリケーション トリガーおよびシステム テーブルにより追跡されないように指定することができます。 アーティクルに対してこのオプションを指定すると、削除は、パブリッシャーやサブスクライバーから追跡またはレプリケートされません。 このオプションは、多くのアプリケーション シナリオをサポートしたり、削除のレプリケーションが不要または望ましくない場合にパフォーマンスの最適化を行うために利用できます。 パフォーマンスは、削除のメタデータを格納しない、削除を同期中に列挙しない、削除をサブスクライバーにレプリケートせずサブスクライバーでも適用しない、という 3 つの方法により向上します。  
  
> [!NOTE]  
>  ダウンロード専用アーティクルを使用するためには、90RTM 以上の互換性レベルが必要になります。  
  
 オプションはパブリケーションを作成する際に指定できます。一部の削除をレプリケートし、バッチによる削除などその他の削除はレプリケートしないことがアプリケーションで必要な場合には、オプションのオン/オフを切り替えられます。 以下の例では、このオプションがどのようにアプリケーションで使用されるかを示します。  
  
-   移動営業部門向けのアプリケーションには、通常、 **SalesOrderHeader**、 **SalesOrderDetail** 、および **Product**などのテーブルがあります。 注文は、サブスクライバーで入力され、次にパブリッシャーにレプリケートされます。パブリッシャーは、頻繁にデータを注文確定システムに送ります。 モバイル ワーカーの多くは、記憶域が制限されたハンドヘルド デバイスを使用しています。パブリッシャーで注文を受けると、サブスクライバーではこれを削除できます。 注文がシステム内ではまだアクティブであるため、削除はパブリッシャーに反映されません。  
  
     このシナリオでは、 **SalesOrderHeader** および **SalesOrderDetail** テーブルに対して、削除は追跡されません。 **Product** テーブルについては、削除を追跡します。これは、パブリッシャーで製品が削除された場合、製品リストを最新に保つために削除をサブスクライバーに送信する必要があるためです。  
  
-   アプリケーションは、 **TransactionHistory**などのテーブルに履歴データを格納できます。テーブルでは、1 年を経過したレコードを定期的に削除します。 サブスクライバーが今月のトランザクションのデータのみを受信するように、テーブルをフィルター選択することもできます。 パブリッシャーで毎月バッチで行われる古いデータの削除は、サブスクライバーとは関係がありませんが、既定では、これらを追跡および列挙します。  
  
     このシナリオでは、バッチ処理が発生する前に、システムでの処理を停止し、アプリケーションで削除の追跡を無効にできます。 処理が完了したら、追跡を再度有効にできます。  
  
> [!IMPORTANT]  
>  パブリッシャーで他の処理が継続している場合は、削除の追跡が無効の間に、サブスクライバーへの反映が必要な削除が発生しないようにする必要があります。  
  
 **削除が追跡されないように指定するには**  
  
-   レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミング: [マージ アーティクルに対して削除を追跡しないように指定する &#40;レプリケーション Transact-SQL プログラミング&#41;](../../../relational-databases/replication/publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションのアーティクルのオプション](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)  
  
  
