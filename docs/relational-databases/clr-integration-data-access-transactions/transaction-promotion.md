---
title: トランザクションの昇格 |Microsoft Docs
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
ms.openlocfilehash: d75bbf1c4d468a0d6c3872a220566d667b059a5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937492"
---
# <a name="transaction-promotion"></a>トランザクションの昇格
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  トランザクションの*昇格*は、必要に応じて完全に再頒布可能なトランザクションに自動的に昇格できる、軽量のローカルトランザクションを記述します。 サーバー側で実行されているデータベース トランザクション内でマネージド ストアド プロシージャが呼び出されると、CLR (共通言語ランタイム) コードはローカル トランザクションのコンテキストで実行されます。  データベース トランザクション内でリモート サーバーへの接続が開かれると、リモート サーバーへの接続が分散トランザクションに参加し、ローカル トランザクションは自動的に分散トランザクションに昇格します。 トランザクションの昇格では、必要になるまで分散トランザクションの作成を遅延し、分散トランザクションのオーバーヘッドを最小限に抑えます。 トランザクションの昇格は、**参加**キーワードを使用して有効になっている場合は自動的に行われ、開発者からの介入は必要ありません。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .NET Framework Data Provider は **、.NET Framework の**system.string 名前空間のクラスを使用して処理されるトランザクションの昇格をサポートしています。  
  
## <a name="the-enlist-keyword"></a>参加キーワード  
 **SqlConnection**オブジェクトの**ConnectionString**プロパティでは、**参加**キーワードがサポートされて**います。** これは、system.string がトランザクションコンテキストを検出し、分散トランザクションに接続を自動的に参加させるかどうかを示します。 このキーワードが true に設定されている場合 (既定の設定)、開かれているスレッドの現在のトランザクション コンテキストに接続が自動参加します。 このキーワードが false に設定されている場合、SqlClient 接続は分散トランザクションとのやり取りを行いません。 接続文字列で [**参加**] が指定されていない場合、接続が開かれたときに接続が検出されると、分散トランザクションに接続が自動的に参加します。  
  
## <a name="distributed-transactions"></a>分散トランザクション  
 通常、分散トランザクションでは、大量のシステム リソースが消費されます。 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) では、分散トランザクションを管理し、それらのトランザクションでアクセスされているすべてのリソース マネージャーを統合します。 一方、トランザクションの昇格は、特殊な形式のシステムトランザクショントランザクションです。これにより、作業を効率的に単純[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]なトランザクションに代行させることができ**ます。** トランザクションの処理に関連する作業を調整[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し **、必要**に応じて完全な分散トランザクションに昇格させ**ます。**  
  
 トランザクションの昇格を使用する利点は、アクティブな**TransactionScope**トランザクションで接続を開いたときに、他の接続が開かれていない場合に、完全な分散トランザクションのオーバーヘッドを増やすのではなく、トランザクションが軽量トランザクションとしてコミットされることです。 **TransactionScope**の詳細については、「 [Using](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)system.string」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
