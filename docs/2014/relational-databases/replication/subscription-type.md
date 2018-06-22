---
title: サブスクリプションの種類 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9a583519bcfabf7540e3b420dc902e2a513aef81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084739"
---
# <a name="subscription-type"></a>サブスクリプションの種類
  マージ レプリケーションには、サーバーとクライアントという 2 つのサブスクリプションの種類があります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでは、これらはグローバルとローカルと呼ばれていました。 サブスクライバーはサーバー サブスクリプションによって次の操作を実行できます。  
  
-   他のサブスクライバーにデータを再パブリッシュする。  
  
-   代わりの同期パートナーを提供する。  
  
-   設定された優先度に応じて競合を解決する。  
  
 ほとんどのサブスクライバーは、この機能を必要とせず、クライアント サブスクリプションを使用できます。 クライアント サブスクリプションは競合の検出と解決ができますが、サブスクライバーには優先度が割り当てられていません。変更によって競合が発生した場合は、変更をパブリッシャーに最初に送信したサブスクライバーが優先されます。  
  
> [!NOTE]  
>  サブスクリプションの種類は、作成後に変更することはできません。  
  
## <a name="options"></a>および  
 **[サブスクリプションのプロパティ]**  
 **[サブスクリプションの種類]** 列のドロップダウン リスト ボックスで、各サブスクライバーに対して、 **[クライアント]** または **[サーバー]** を選択します。 サブスクライバーでサーバー サブスクリプションを使用する場合は、 **[競合解決の優先度]** 列に 0 ～ 99.99 の範囲の数値を入力します。数字が大きいほどサブスクライバーに対する優先度が高くなります。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  