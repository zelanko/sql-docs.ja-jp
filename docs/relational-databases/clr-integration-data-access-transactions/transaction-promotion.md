---
title: トランザクションの昇格 |Microsoft Docs
description: SQL Server CLR 統合では、軽量のローカルトランザクションをトランザクション昇格によって完全に再頒布可能なトランザクションに昇格させることができます。
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
ms.openlocfilehash: 1267a916e1f3ed9bbcdf3e03240f5fcc39b7eb1b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765354"
---
# <a name="transaction-promotion"></a>トランザクションの昇格
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  トランザクションの*昇格*は、必要に応じて完全に再頒布可能なトランザクションに自動的に昇格できる、軽量のローカルトランザクションを記述します。 サーバー側で実行されているデータベース トランザクション内でマネージド ストアド プロシージャが呼び出されると、CLR (共通言語ランタイム) コードはローカル トランザクションのコンテキストで実行されます。  データベース トランザクション内でリモート サーバーへの接続が開かれると、リモート サーバーへの接続が分散トランザクションに参加し、ローカル トランザクションは自動的に分散トランザクションに昇格します。 トランザクションの昇格では、必要になるまで分散トランザクションの作成を遅延し、分散トランザクションのオーバーヘッドを最小限に抑えます。 トランザクションの昇格は、**参加**キーワードを使用して有効になっている場合は自動的に行われ、開発者からの介入は必要ありません。 の .NET Framework Data Provider は、.NET Framework の system.string [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名前空間のクラスを使用して処理**System.Data.SqlClient**されるトランザクションの昇格をサポートしています。  
  
## <a name="the-enlist-keyword"></a>参加キーワード  
 **SqlConnection**オブジェクトの**ConnectionString**プロパティでは、**参加**キーワードがサポートされて**います。** これは、system.string がトランザクションコンテキストを検出し、分散トランザクションに接続を自動的に参加させるかどうかを示します。 このキーワードが true に設定されている場合 (既定の設定)、開かれているスレッドの現在のトランザクション コンテキストに接続が自動参加します。 このキーワードが false に設定されている場合、SqlClient 接続は分散トランザクションとのやり取りを行いません。 接続文字列で [**参加**] が指定されていない場合、接続が開かれたときに接続が検出されると、分散トランザクションに接続が自動的に参加します。  
  
## <a name="distributed-transactions"></a>分散トランザクション  
 通常、分散トランザクションでは、大量のシステム リソースが消費されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) では、分散トランザクションを管理し、それらのトランザクションでアクセスされているすべてのリソース マネージャーを統合します。 一方、トランザクションの昇格は、特殊な形式のシステムトランザクショントランザクションです。これにより、作業を効率的に単純なトランザクションに代行させることができ**ます。** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **System.Transactions** **System.Data.SqlClient** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクションの処理に関連する作業を調整し、必要に応じて完全な分散トランザクションに昇格させます。  
  
 トランザクションの昇格を使用する利点は、アクティブな**TransactionScope**トランザクションで接続を開いたときに、他の接続が開かれていない場合に、完全な分散トランザクションのオーバーヘッドを増やすのではなく、トランザクションが軽量トランザクションとしてコミットされることです。 **TransactionScope**の詳細については、「 [Using](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)system.string」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
