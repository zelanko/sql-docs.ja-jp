---
title: 取引プロモーション |マイクロソフトドキュメント
description: SQL Server CLR 統合では、トランザクションの昇格を通じて、軽量のローカル トランザクションを完全に分散可能なトランザクションに昇格できます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
author: rothja
ms.author: jroth
ms.openlocfilehash: e77409f6bf6c71363e030f29f86f41205dd4a0f0
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487485"
---
# <a name="transaction-promotion"></a>トランザクションの昇格
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  トランザクション*のプロモーション*は、必要に応じて完全に分配可能なトランザクションに自動的に昇格できる、軽量なローカル トランザクションを表します。 サーバー側で実行されているデータベース トランザクション内でマネージド ストアド プロシージャが呼び出されると、CLR (共通言語ランタイム) コードはローカル トランザクションのコンテキストで実行されます。  データベース トランザクション内でリモート サーバーへの接続が開かれると、リモート サーバーへの接続が分散トランザクションに参加し、ローカル トランザクションは自動的に分散トランザクションに昇格します。 トランザクションの昇格では、必要になるまで分散トランザクションの作成を遅延し、分散トランザクションのオーバーヘッドを最小限に抑えます。 Enlist**キーワードを**使用して有効にされている場合、トランザクションの昇格は自動的に行われ、開発者の介入は必要ありません。 .NET Framework データ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダーは、.NET Framework**の名前空間**のクラスを介して処理されるトランザクションの昇格をサポートします。  
  
## <a name="the-enlist-keyword"></a>参加キーワード  
 プロパティ**は****System.Data.SqlClient****、SqlConnection**オブジェクトの**Enlist**キーワードをサポートしています。 このキーワードが true に設定されている場合 (既定の設定)、開かれているスレッドの現在のトランザクション コンテキストに接続が自動参加します。 このキーワードが false に設定されている場合、SqlClient 接続は分散トランザクションとのやり取りを行いません。 接続文字列に**Enlist**が指定されていない場合、接続が開かれた時点で接続が検出された場合、接続は自動的に分散トランザクションに参加します。  
  
## <a name="distributed-transactions"></a>分散トランザクション  
 通常、分散トランザクションでは、大量のシステム リソースが消費されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) では、分散トランザクションを管理し、それらのトランザクションでアクセスされているすべてのリソース マネージャーを統合します。 一方、トランザクションのプロモーションは、作業を単純な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションに効果的に委任する特別な形式の**System.Transaction トランザクション**です。 **トランザクション**、 **System.Data.SqlClient**、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションの処理に関連する作業を調整し、必要に応じてトランザクションを完全な分散トランザクションに昇格させます。  
  
 トランザクションの昇格を使用する利点は、アクティブな**TransactionScope**トランザクションで接続が開かれ、他の接続が開かれたとき、トランザクションは、完全な分散トランザクションの追加オーバーヘッドを発生させるのではなく、軽量トランザクションとしてコミットすることです。 **トランザクション スコープ**の詳細については、「 [System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)の使用 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
