---
title: MSSQL_REPL027183 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 78a3ab8b69c29d49906c6f144ef75d2fb6cf0256
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070699"
---
# <a name="mssqlrepl027183"></a>MSSQL_REPL027183
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|27183|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|マージ処理で、パラメーター化された行フィルターを使用して、アーティクル内の変更情報を列挙できませんでした。 このエラーが継続して発生する場合、このプロセスのクエリ タイムアウト値を増やし、パブリケーションの保有期間を減少し、パブリッシュされたテーブルのインデックスを強化してください。|  
  
## <a name="explanation"></a>説明  
 このエラーは、フィルター選択されたパブリケーションでの変更を処理中に、マージ エージェント タイムアウトになると発生します。 このタイムアウトは、次のいずれかの問題点により生じた可能性があります。  
  
-   事前計算済みパーティションの最適化の未使用  
  
-   フィルター選択に使用される列のインデックスの断片化  
  
-   **MSmerge_tombstone**、 **MSmerge_contents**、 **MSmerge_genhistory**などの、大規模なマージ メタデータ テーブル  
  
-   一意キーで結合されていないフィルター選択されたテーブルや多くのテーブルを含む結合フィルター  
  
## <a name="user-action"></a>ユーザーの操作  
 問題を解決するには、以下の操作を実行します。  
  
-   マージ エージェントの **-QueryTimeOut** パラメーターの値を大きくし、エラーの原因となっている根本的な問題に対処する間、処理を継続できるようにします。 エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。 詳細については、以下をご覧ください。  
  
    -   [レプリケーション エージェント プロファイルの操作](agents/replication-agent-profiles.md)  
  
    -   [レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [レプリケーション エージェント実行可能ファイルの概念](concepts/replication-agent-executables-concepts.md)。  
  
-   可能であれば、事前計算済みパーティションの最適化を使用します。 既定では、この最適化は、多くのパブリケーションの要件が満たされている場合に使用されます。 これらの要件の詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。 パブリケーションがこれらの要件を満たしていない場合は、パブリケーションを再設計することを検討してください。  
  
-   パブリケーションの保有期間をできる限り低い設定に指定します。保有期間に達するまで、レプリケーションはパブリケーション データベースおよびサブスクリプション データベースでメタデータをクリーンアップできません。 詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」をご覧ください。  
  
-   マージ レプリケーションのメンテナンスの一環として、マージ レプリケーションに関連付けられたシステム テーブル **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**、および **MSmerge_past_partition_mappings**の増大を必要に応じて確認します。 定期的にこれらのテーブルのインデックスを再設定します。 詳細については、「 [インデックスの再編成と再構築](../indexes/indexes.md)」を参照してください。  
  
-   フィルター選択に使用する列のインデックスが適切であることを確認し、必要に応じてインデックスを再構築します。 詳細については、「 [インデックスの再編成と再構築](../indexes/indexes.md)」を参照してください。  
  
-   一意な列に基づく結合フィルターの **join_unique_key** プロパティを設定します。 詳しくは、「 [Join Filters](merge/join-filters.md)」をご覧ください。  
  
-   結合フィルター階層のテーブル数を制限します。 テーブルが 5 つ以上の結合フィルターを生成する場合は、小さなテーブル、変更されないテーブル、プライマリ参照テーブルはフィルター選択しないという別の解決策を検討してください。 結合フィルターは、サブスクリプション間でパーティション分割する必要のあるテーブル間でのみ使用します。  
  
-   同期を行うまでの間はフィルター選択されたテーブルへの変更を少なくするか、マージ エージェントをより頻繁に実行します。 同期処理のスケジュール設定の詳細については、「 [Specify Synchronization Schedules](specify-synchronization-schedules.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  