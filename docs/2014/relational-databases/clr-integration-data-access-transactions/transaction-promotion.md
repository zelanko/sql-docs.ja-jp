---
title: トランザクションの昇格 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 74beef45bcf29f78b800100e2c3c8ec14c301435
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085453"
---
# <a name="transaction-promotion"></a>トランザクションの昇格
  トランザクション*プロモーション*自動的に昇格できる完全な分散トランザクションを必要に応じて、軽量のローカル トランザクションを示します。 サーバー側で実行されているデータベース トランザクション内でマネージ ストアド プロシージャが呼び出されると、CLR (共通言語ランタイム) コードはローカル トランザクションのコンテキストで実行されます。  データベース トランザクション内でリモート サーバーへの接続が開かれると、リモート サーバーへの接続が分散トランザクションに参加し、ローカル トランザクションは自動的に分散トランザクションに昇格します。 トランザクションの昇格では、必要になるまで分散トランザクションの作成を遅延し、分散トランザクションのオーバーヘッドを最小限に抑えます。 トランザクションの昇格が `Enlist` キーワードを使用して有効になっている場合、トランザクションの昇格は自動的に行われるので、開発者の介入は必要ありません。 .NET Framework [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用データ プロバイダーでは、トランザクションの昇格がサポートされます。トランザクションの昇格は、.NET Framework の `System.Data.SqlClient` 名前空間のクラスによって行われます。  
  
## <a name="the-enlist-keyword"></a>Enlist キーワード  
 `ConnectionString` オブジェクトの `SqlConnection` プロパティでは、`Enlist` キーワードがサポートされます。このキーワードは、`System.Data.SqlClient` 名前空間で、トランザクション コンテキストを検出し、自動的に接続を分散トランザクションに参加させるかどうかを示すものです。 このキーワードが true に設定されている場合 (既定の設定)、開かれているスレッドの現在のトランザクション コンテキストに接続が自動参加します。 このキーワードが false に設定されている場合、SqlClient 接続は分散トランザクションとのやり取りを行いません。 接続文字列で `Enlist` キーワードが指定されていない場合は、接続が開かれたときに分散トランザクションが検出されると、接続は分散トランザクションに自動参加します。  
  
## <a name="distributed-transactions"></a>分散トランザクション  
 通常、分散トランザクションでは、大量のシステム リソースが消費されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) では、分散トランザクションを管理し、それらのトランザクションでアクセスされているすべてのリソース マネージャーを統合します。 これに対し、トランザクションの昇格は、`System.Transactions` トランザクションの特殊な形式であり、作業を単純な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクションに効率よく委任します。 `System.Transactions`、`System.Data.SqlClient`、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、トランザクションの処理に関連する作業を調整し、必要に応じて、トランザクションを完全な分散トランザクションに昇格します。  
  
 トランザクションの昇格を使用するメリットとして、1 つのアクティブな `TransactionScope` で接続が開かれていて、他の接続が開かれていない場合、そのトランザクションは軽量なトランザクションとしてコミットされ、完全な分散トランザクションとしてのオーバーヘッドが発生しないという点があります。 詳細については`TransactionScope`を参照してください[を使用して System.Transactions](../native-client-ole-db-transactions/transactions.md)です。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](clr-integration-and-transactions.md)  
  
  