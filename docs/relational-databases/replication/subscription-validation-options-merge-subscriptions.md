---
title: '[サブスクリプションの検証オプション](マージ サブスクリプション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5f66bd39715420d4eecd261e18b4589ec1eb60ab
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="subscription-validation-options-merge-subscriptions"></a>[サブスクリプションの検証オプション]\(マージ サブスクリプション)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **[サブスクリプションの検証オプション]** ダイアログ ボックスを使用すると、検証の際に行数だけを使用するか、行数とバイナリ チェックサムを使用するかを指定できます。  
  
## <a name="options"></a>および  
 **[行数のみを確認する]**  
 選択すると、サブスクライバー側のテーブルとパブリッシャー側のテーブルの行数が同じかどうかを確認できます。 この方法では、行の内容が一致するかどうかは確認されません。 行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。  
  
 **[行数を確認し、行データを評価するためにチェックサムを比較する (すべてのサブスクライバーは SQL Server 2000 以降を実行しているサーバー)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。 このオプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]では無効です。  
  
## <a name="see-also"></a>参照  
 [サブスクライバーでのデータの検証](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  
