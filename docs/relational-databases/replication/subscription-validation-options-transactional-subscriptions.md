---
title: "[サブスクリプションの検証オプション](トランザクション サブスクリプション) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.validate.options.f1
helpviewer_keywords: Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77e1e620f4adc3fc44a937a12b2ab74dc3302bc0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>[サブスクリプションの検証オプション] (トランザクション サブスクリプション)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] **[サブスクリプションの検証オプション]** ダイアログ ボックスを使用すると、検証に行数のみを使用するか、行数とバイナリ チェックサムを使用するかを指定できます。  
  
## <a name="options"></a>オプション  
 **[サブスクライバーとパブリッシャーでレプリケートされたデータの行数が同じであることを確認します。]**  
 実行する行数の検証の種類を選択します。 Oracle パブリケーションの場合、使用できるオプションは **[テーブルに直接クエリすることにより、実際の行数を計算する]**のみとなります。  
  
 **[行データを比較するためにチェックサムを比較する (この処理には時間がかかります)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。  
  
 **[検証完了後にディストリビューション エージェントを停止する]**  
 既定では、ディストリビューション エージェントは継続的に実行されます。 検証の実行後にエージェントを停止するには、このオプションを選択します。 これにより、サブスクライバーへのデータのレプリケートを継続する前に、検証が成功したかどうかをチェックできます。  
  
## <a name="see-also"></a>参照  
 [サブスクライバーでのデータの検証](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  
