---
title: "[すべてのサブスクリプションの検証] | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.validate.allsubscriptions.f1
helpviewer_keywords: Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56b77ea98640f649458a6bd25edf19d47287421c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="validate-all-subscriptions"></a>[すべてのサブスクリプションの検証]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[すべてのサブスクリプションの検証]** ダイアログ ボックスを使用すると、各サブスクリプションのマージ エージェントを次に実行するときに、マージ パブリケーションへのサブスクリプションをすべて検証するように指定できます。 検証の結果はレプリケーション モニターに表示されます。 詳細については、「 [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md)」を参照してください。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクリプションを右クリックし、 **[サブスクリプションの検証]**をクリックすることでも、1 つのサブスクリプションを検証することができます。  
  
## <a name="options"></a>オプション  
 **[行数のみを確認する]**  
 選択すると、サブスクライバー側のテーブルとパブリッシャー側のテーブルの行数が同じかどうかを確認できます。 この方法では、行の内容が一致するかどうかは確認されません。 行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。  
  
 **[行数を確認し、行データを評価するためにチェックサムを比較する (すべてのサブスクライバーは SQL Server 2000 以降を実行しているサーバー)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。 このオプションは [!INCLUDE[ssEW](../../includes/ssew-md.md)]では無効です。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  
