---
title: "CLR 統合とトランザクション |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b6975d640f1c65c945337432d18fa2bfbc03e971
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="clr-integration-and-transactions"></a>CLR 統合とトランザクション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**System.Transactions**名前空間は ADO.NET と完全に統合される新しいトランザクション フレームワークを提供し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語ランタイム (CLR) 統合します。 **System.Transactions**と ADO.NET は連携して拡張およびローカル トランザクションと分散トランザクションのマネージ アプリケーションでの使用を単純化します。  
  
> [!NOTE]  
>  CLR ユーザー定義プロシージャ (UDP) は、このプロシージャが実行されているサーバーへの接続 (ループバック接続) を確立して、同じトランザクションに参加することができません。 この操作を試みると、接続試行がブロックされ、制御は UDP に返されません。 これにより、UDP でタイムアウト エラー (メッセージ 1206) が発生します。  
  
 トランザクションと .NET Framework の詳細については、.NET Framework SDK の「トランザクションの実行」と「トランザクションの利用」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [トランザクションの昇格](../../relational-databases/clr-integration-data-access-transactions/transaction-promotion.md)  
 トランザクションを昇格する機能とこの機能の使用方法について説明します。  
  
 [現在のトランザクションへのアクセス](../../relational-databases/clr-integration-data-access-transactions/accessing-the-current-transaction.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインプロセスで現在実行中のトランザクションにアクセスする方法について説明します。  
  
 [System.Transactions の使用](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)  
 使用する方法について説明します、 **System.Transactions**マネージ アプリケーションでのアプリケーション プログラミング インターフェイス (API)。  
  
 [トランザクションの有効期間](../../relational-databases/clr-integration-data-access-transactions/transaction-lifetimes.md)  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで開始されたトランザクションと、CLR アプリケーションで開始されたトランザクションの有効期間の違いについて説明します。  
  
## <a name="see-also"></a>参照  
 [CLR データベース オブジェクトからのデータ アクセス](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
