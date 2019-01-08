---
title: マージ レプリケーションの競合の検出および解決 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 8d29ccc697bb34b0872f0a75b0b03c7db82faea4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52786054"
---
# <a name="detect-and-resolve-merge-replication-conflicts"></a>マージ レプリケーションの競合の検出と解決
  パブリッシャーとサブスクライバーが接続され、同期が発生すると、マージ エージェントによって競合の検出が行われます。 競合が検出された場合、マージ エージェントは競合回避モジュールを使用して、どのデータを受け入れて他のサイトに反映するかを決定します。  
  
> [!NOTE]  
>  サブスクライバーがパブリッシャーと同期している場合でも、サブスクライバーとパブリッシャーでの更新よりも、別のサブスクライバーの更新で競合が発生することがよくあります。  
  
 マージ レプリケーションでは、競合を検出して解決するためのさまざまなメソッドが用意されています。 ほとんどのアプリケーションの場合、次の既定のメソッドが適切です。  
  
-   競合がパブリッシャーとサブスクライバーの間で発生した場合、パブリッシャーの変更は保存され、サブスクライバーの変更は破棄されます。  
  
-   クライアント サブスクリプション (プル サブスクリプションの既定の種類) を使用している 2 つのサブスクライバー間で競合が発生した場合は、パブリッシャーと同期する最初のサブスクライバーからの変更が保存され、2 番目のサブスクライバーからの変更は破棄されます。 クライアントとサーバーのサブスクリプションの指定の詳細については、「[Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)」 (マージ サブスクリプションの種類と競合解決プロパティの指定 (SQL Server Management Studio)) を参照してください。  
  
-   サーバー サブスクリプション (プッシュ サブスクリプションの既定の種類) を使用している 2 つのサブスクライバー間で競合が発生した場合は、優先度が高い方のサブスクライバーからの変更が保存され、2 番目のサブスクライバーからの変更は破棄されます。 優先度値が同じである場合は、パブリッシャーと同期する最初のサブスクライバーからの変更が保存されます。  
  
 マージ レプリケーションにおける競合の検出と解決の詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションのアーティクル オプション](article-options-for-merge-replication.md)   
 [パブリケーションのサブスクライブ](../subscribe-to-publications.md)  
  
  
