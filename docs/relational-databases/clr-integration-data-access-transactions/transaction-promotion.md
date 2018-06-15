---
title: トランザクションの昇格 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 742ff5f5785fea2c3652fc88e78d5cefc2090281
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918267"
---
# <a name="transaction-promotion"></a>トランザクションの昇格
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  トランザクション*プロモーション*自動的に昇格できる完全な分散トランザクションを必要に応じて、軽量のローカル トランザクションを示します。 サーバー側で実行されているデータベース トランザクション内でマネージ ストアド プロシージャが呼び出されると、CLR (共通言語ランタイム) コードはローカル トランザクションのコンテキストで実行されます。  データベース トランザクション内でリモート サーバーへの接続が開かれると、リモート サーバーへの接続が分散トランザクションに参加し、ローカル トランザクションは自動的に分散トランザクションに昇格します。 トランザクションの昇格では、必要になるまで分散トランザクションの作成を遅延し、分散トランザクションのオーバーヘッドを最小限に抑えます。 トランザクションの昇格は自動的を使用して有効にする場合、 **Enlist**キーワードでは、開発者による介入は必要ありません。 .NET Framework Data Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションの昇格、.NET Framework のクラスを介して処理のサポートを提供**System.Data.SqlClient**名前空間。  
  
## <a name="the-enlist-keyword"></a>Enlist キーワード  
 **ConnectionString**のプロパティ、 **SqlConnection**オブジェクトのサポート、 **Enlist**かを示すキーワードかどうか**System.Data.SqlClient**トランザクションのコンテキストを検出し、分散トランザクションに、接続を自動的に登録します。 このキーワードが true に設定されている場合 (既定の設定)、開かれているスレッドの現在のトランザクション コンテキストに接続が自動参加します。 このキーワードが false に設定されている場合、SqlClient 接続は分散トランザクションとのやり取りを行いません。 場合**Enlist**が指定されていない接続文字列で接続は接続を開いた時点でいずれかが検出された場合、自動的に分散トランザクションに参加します。  
  
## <a name="distributed-transactions"></a>分散トランザクション  
 通常、分散トランザクションでは、大量のシステム リソースが消費されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) では、分散トランザクションを管理し、それらのトランザクションでアクセスされているすべてのリソース マネージャーを統合します。 その一方は、特殊な形式のトランザクションの昇格、 **System.Transactions**は単に作業を効果的に委任トランザクション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションです。 **System.Transactions**、 **System.Data.SqlClient**、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]必要に応じて、完全な分散トランザクションに昇格、トランザクションの処理に必要な作業を調整します。  
  
 アクティブな接続が開かれたときにトランザクションの昇格を使用する利点は**TransactionScope**トランザクション、および他の接続が開くと、トランザクションが軽量なトランザクションとしてコミットされるなく完全な分散トランザクションによるオーバーヘッドが発生します。 詳細については**TransactionScope**を参照してください[を使用して System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)です。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
