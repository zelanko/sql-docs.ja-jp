---
title: SQL Server 分散再生 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Distributed Replay
- SQL Server Distributed Replay
ms.assetid: 58ef7016-b105-42c2-90a0-364f411849a4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1991b9a960d0314b00d2a5cd45997e0502890698
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048517"
---
# <a name="sql-server-distributed-replay"></a>SQL Server Distributed Replay
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生機能を使用すると、将来の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のアップグレードによる影響を評価できます。 また、ハードウェアとオペレーティング システムのアップグレード、および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のチューニングの影響を評価する場合にも使用できます。

## <a name="benefits-of-distributed-replay"></a>Distributed Replay の利点
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]と同様に、Distributed Replay を使用して、アップグレードされたテスト環境に対してキャプチャしたトレースを再生できます。 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]と異なるのは、Distributed Replay は 1 台のコンピューターからのワークロードの再生に限定されないことです。

 Distributed Replay では、[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] よりもスケーラブルなソリューションが提供されます。 Distributed Replay を使用すると、複数のコンピューターからのワークロードを再生し、ミッションクリティカルなワークロードをより正確にシミュレートできます。

 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生機能では、複数のコンピューターを使用してトレース データを再生し、ミッション クリティカルなワークロードをシミュレートできます。 Distributed Replay は、アプリケーション互換性テスト、パフォーマンス テスト、またはキャパシティ プランニングに使用できます。

## <a name="when-to-use-distributed-replay"></a>Distributed Replay を使用する状況
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] と Distributed Replay は、提供する機能が一部重複しています。

 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] を使用して、アップグレードされたテスト環境に対してキャプチャしたトレースを再生できます。 また、再生結果を分析して、潜在的な機能とパフォーマンスの非互換性を調べることができます。 ただし、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] で再生できるのは、1 台のコンピューターからのワークロードのみです。 アクティブなコンカレント接続が多数あるか、またはスループットが高い集中型の OLTP アプリケーションを再生すると、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] ではリソースのボトルネックが発生する可能性があります。

 Distributed Replay では、[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] よりもスケーラブルなソリューションが提供されます。 Distributed Replay を使用すると、複数のコンピューターからのワークロードを再生し、ミッションクリティカルなワークロードをより正確にシミュレートできます。

 次の表では、各ツールを使用する状況について説明します。

|ツール|使用する状況|
|----------|---------------|
|[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]|1 台のコンピューター上で、従来の再生のメカニズムを使用する場合。 特に、 **[ステップ]** 、 **[カーソルまで実行]** 、 **[ブレークポイントの設定/解除]** など、1 行ずつのデバッグ機能が必要な場合。<br /><br /> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] トレースを再生する場合。|
|Distributed Replay|アプリケーションの互換性を評価する場合。 たとえば、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] とオペレーティング システムのアップグレード シナリオ、ハードウェアのアップグレード、インデックス チューニングをテストする場合などがあります。<br /><br /> キャプチャしたトレースのコンカレンシーが非常に高いため、1 つの再生クライアントで十分にシミュレートできない場合。|

## <a name="distributed-replay-concepts"></a>Distributed Replay の概念
 Distributed Replay 環境は次のコンポーネントで構成されます。

-   **分散再生管理ツール**: `DReplay.exe` 分散再生コントローラーとの通信に使用されるコンソールアプリケーション。 Distributed Replay を制御するには管理ツールを使用します。

-   **分散再生コントローラー**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生コントローラーという名前の Windows サービスを実行するコンピューター。 分散再生コントローラーは、分散再生クライアントのアクションを統制します。 各分散再生環境には、コントローラーのインスタンスを 1 つだけ置くことができます。

-   **分散再生クライアント**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生クライアントという名前の Windows サービスを実行する 1 つまたは複数の (物理または仮想) コンピューター。 分散再生クライアントは連携して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに対するワークロードをシミュレートします。 各分散再生環境には、1 つまたは複数のクライアントを置くことができます。

-   **対象サーバー**:トレース データを再生する際に分散再生クライアントが使用できる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス。 ターゲット サーバーはテスト環境に配置することをお勧めします。

 Distributed Replay の管理ツール、コントローラー、およびクライアントは、異なるコンピューターにインストールすることも、同じコンピューターにインストールすることもできます。 同じコンピューターで実行できる Distributed Replay Controller サービスまたは Distributed Replay Client サービスのインスタンスは 1 つだけです。

 次の図は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay の物理アーキテクチャを示したものです。

 ![分散再生アーキテクチャ](../../database-engine/media/distributedreplayarch.gif "分散再生アーキテクチャ")

## <a name="distributed-replay-tasks"></a>Distributed Replay のタスク

|タスクの説明|トピック|
|----------------------|-----------|
|Distributed Replay を構成する方法について説明します。|[分散再生の構成](configure-distributed-replay.md)|
|入力トレース データを準備する方法について説明します。|[入力トレース データの準備](prepare-the-input-trace-data.md)|
|トレース データを再生する方法について説明します。|[トレース データの再生](replay-trace-data.md)|
|Distributed Replay トレース データの結果を確認する方法について説明します。|[再生結果の確認](review-the-replay-results.md)|
|管理ツールを使用して、コントローラー上の操作を開始、監視、取り消す方法について説明します。|[管理ツール コマンド ライン オプション &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md)|

## <a name="see-also"></a>参照
 [SQL Server 分散再生を使用して](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2)[分散再生フォーラムを SQL Server](https://social.technet.microsoft.com/Forums/sl/sqldru/)して、分散再生[を使用して SQL Server をロードテストし、をロードテストします。第1部](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)


