---
title: マージ レプリケーションの競合の検出および解決 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ada98028bface5ff05c54b89db4c0aacb6173636
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47599044"
---
# <a name="advanced-merge-replication---resolve-merge-replication-conflicts"></a>マージ レプリケーションの詳細 - マージ レプリケーションの競合の解決
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  パブリッシャーとサブスクライバーが接続され、同期が発生すると、マージ エージェントによって競合の検出が行われます。 競合が検出された場合、マージ エージェントは競合回避モジュールを使用して、どのデータを受け入れて他のサイトに反映するかを決定します。  
  
> [!NOTE]  
>  サブスクライバーがパブリッシャーと同期している場合でも、サブスクライバーとパブリッシャーでの更新よりも、別のサブスクライバーの更新で競合が発生することがよくあります。  
  
 マージ レプリケーションでは、競合を検出して解決するためのさまざまなメソッドが用意されています。 ほとんどのアプリケーションの場合、次の既定のメソッドが適切です。  
  
-   競合がパブリッシャーとサブスクライバーの間で発生した場合、パブリッシャーの変更は保存され、サブスクライバーの変更は破棄されます。  
  
-   クライアント サブスクリプション (プル サブスクリプションの既定の種類) を使用している 2 つのサブスクライバー間で競合が発生した場合は、パブリッシャーと同期する最初のサブスクライバーからの変更が保存され、2 番目のサブスクライバーからの変更は破棄されます。 クライアントとサーバーのサブスクリプションの指定の詳細については、「[Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)](../../../relational-databases/replication/specify-a-merge-subscription-type-and-conflict-resolution-priority.md)」 (マージ サブスクリプションの種類と競合解決プロパティの指定 (SQL Server Management Studio)) を参照してください。  
  
-   サーバー サブスクリプション (プッシュ サブスクリプションの既定の種類) を使用している 2 つのサブスクライバー間で競合が発生した場合は、優先度が高い方のサブスクライバーからの変更が保存され、2 番目のサブスクライバーからの変更は破棄されます。 優先度値が同じである場合は、パブリッシャーと同期する最初のサブスクライバーからの変更が保存されます。  
  
 マージ レプリケーションにおける競合の検出と解決の詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションのアーティクル オプション](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [パブリケーションのサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  
