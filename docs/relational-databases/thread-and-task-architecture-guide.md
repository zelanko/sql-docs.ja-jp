---
title: スレッドおよびタスクのアーキテクチャ ガイド | Microsoft Docs
ms.custom: ''
ms.date: 11/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- guide, thread and task architecture
- thread and task architecture guide
ms.assetid: 925b42e0-c5ea-4829-8ece-a53c6cddad3b
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2d0c25e433fd9e311908d1759bbe75a1e1a1f045
ms.sourcegitcommit: 7e828cd92749899f4e1e45ef858ceb9a88ba4b6a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2018
ms.locfileid: "51629593"
---
# <a name="thread-and-task-architecture-guide"></a>スレッドおよびタスクのアーキテクチャ ガイド
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

スレッドは、同時に実行される複数の実行パスにアプリケーション ロジックを分割できるオペレーティング システムの機能です。 この機能は、複雑なアプリケーションに同時に実行できるタスクが多数ある場合に役立ちます。 

オペレーティング システムがアプリケーションのインスタンスを実行するときは、プロセスという単位が作成され、インスタンスを管理します。 プロセスには実行のためのスレッドが 1 つあります。 これは、アプリケーション コードで実行される一連のプログラミング命令です。 たとえば、直列に実行できる 1 つの命令セットで構成される単純なアプリケーションの場合、実行パスまたはスレッドはアプリケーション全体で 1 つあるだけです。 より複雑なアプリケーションの場合は、直列ではなく、並行して実行できる複数のタスクで構成されていることがあります。 その際、タスクごとに個別のプロセスを起動することで並列処理を実現できますが、 プロセスの起動には大量のリソースが必要です。 そこで、スレッドを個別に起動することができます。 これにより、リソースの消費を比較的抑えることができます。 また、各スレッドは、プロセスに関連付けられた他のスレッドに依存することなく、その実行スケジュールを設定できます。

CPU が 1 基しか搭載されていないコンピューターであっても、スレッドによって、複雑なアプリケーションが CPU をより効率的に使用できるようになります。 CPU が 1 基の場合、一度に実行できるスレッドは 1 つだけです。 あるスレッドが、ディスクの読み書きなど、CPU を使用しない処理を長時間にわたって実行している場合、この処理が終了するまで他のスレッドを実行できます。 処理の終了を待っている間に他のスレッドを実行できるようにすることで、アプリケーションは CPU を最大限に使用できます。 データベース サーバーなど、ディスク I/O が多発するマルチユーザー アプリケーションの場合、特にそのことが当てはまります。 複数のマイクロプロセッサまたは CPU が搭載されているコンピューターの場合、各 CPU が 1 つのスレッドを同時に実行できます。 たとえば、CPU を 8 基搭載したコンピューターは同時に 8 個のスレッドを実行できます。

## <a name="sql-server-batch-or-task-scheduling"></a>SQL Server のバッチまたはタスクのスケジュール設定

### <a name="allocating-threads-to-a-cpu"></a>CPU へのスレッドの割り当て
既定では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の各インスタンスによってそれぞれのスレッドが起動され、オペレーティング システムによって、コンピューターに搭載されている CPU に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスのスレッドを負荷に基づいて分散させます。 処理関係がオペレーティング システム レベルで有効な場合、オペレーティング システムによって各スレッドが特定の CPU に割り当てられます。 これに対し、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] は、スレッドをプロセッサ (CPU) 間で分散させるスケジューラに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ワーカー スレッドを割り当てます。
    
マルチタスク処理を実行するには、たとえば、複数のアプリケーションでプロセッサの同じセットにアクセスする場合、オペレーティング システムによって異なるプロセッサ間でプロセスのスレッドを移動させることがあります。 オペレーティング システムにとっては効率的であっても、この操作で各プロセッサのキャッシュに繰り返しデータが再読み込みされるため、システムの負荷が高くなり、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のパフォーマンスが低下する場合があります。 このような状況では、特定のスレッドにプロセッサを割り当てることで、プロセッサの再読み込みを回避し、プロセッサ間でのスレッドの移行回数を少なくできるため、コンテキストの切り替えを減らしてパフォーマンスを改善できます。このようなスレッドとプロセッサ間の関連付けを "プロセッサ関係 (processor affinity)" と言います。 関係 (affinity) が有効な場合、オペレーティング システムにより、各スレッドが特定の CPU に割り当てられます。 

[affinity mask オプション](../database-engine/configure-windows/affinity-mask-server-configuration-option.md)を設定するには、[ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) を使用します。 関係マスク (affinity mask) が設定されていない場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスでは、マスク オフに指定されていない複数のスケジューラにワーカー スレッドが均等に割り当てられます。

> [!CAUTION]
> オペレーティング システムでの CPU 関係の構成と、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] での関係マスクの構成は、同時に行わないようにしてください。 この 2 つの設定は、同じ効果をねらったものであり、これらの構成間に一貫性がない場合は、予期しない結果を招く可能性があります。 詳細については、[affinity mask オプション](../database-engine/configure-windows/affinity-mask-server-configuration-option.md)に関するページを参照してださい。

スレッド プールは、多数のクライアントがサーバーに接続されている場合のパフォーマンスの最適化に役立ちます。 通常、クエリ要求ごとに個別のオペレーティング システム スレッドが作成されます。 ただし、サーバーへの接続が数百にもなる場合、クエリ要求ごとに 1 つのスレッドを使用すると大量のシステム リソースが消費されることがあります。 [max worker threads オプション](..//database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)を使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によってワーカー スレッドのプールが作成され、多数のクエリ要求を処理できるようになります。これにより、パフォーマンスが向上します。 

### <a name="using-the-lightweight-pooling-option"></a>lightweight pooling オプションの使用
スレッド コンテキストの切り替えにかかわるオーバーヘッドは、それほど大きくない可能性があります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のほとんどのインスタンスでは、lightweight pooling オプションを 0 または 1 のどちらに設定してもパフォーマンスに違いはありません。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスが[簡易プーリング (lightweight pooling) ](../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)から利点を得る唯一の条件は、次の特性を備えたコンピューター上で実行されることです。    
* 大規模なマルチ CPU サーバーを備えている
* すべての CPU がほぼ最大容量で稼動している
* 高いレベルのコンテキスト切り替えが行われている

このようなシステムでは、lightweight pooling 値が 1 に設定されていると、パフォーマンスがわずかに向上することがあります。

> [!IMPORTANT]
> ルーチン処理にファイバー モード スケジューリングを使用しないでください。 これは、コンテキストの切り替えがもたらす本来の利点が損なわれることでパフォーマンスが低下する場合があり、ファイバー モードでは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の一部のコンポーネントが正常に機能しないためです。 詳細については、[簡易プーリング](../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)に関するページを参照してください。

## <a name="thread-and-fiber-execution"></a>スレッドとファイバーの実行
Microsoft Windows では、1 から 31 までの優先度の数値に基づいてスレッドの実行がスケジュール設定されます。 ゼロは、オペレーティング システム用に予約されています。 複数のスレッドが実行を待機している場合、最も優先度の高いスレッドから先に実行されます。

既定では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の各インスタンスの優先度は 7 です。優先度が 7 のスレッドは、優先度が通常のスレッドと見なされます。 この既定値により、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スレッドには、他のアプリケーションに悪影響を及ぼさずに十分な CPU リソースを得られるだけの高い優先度が与えられます。 

[priority boost](../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md) 構成オプションを使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスのスレッドの優先度を 13 まで上げることができます。 優先度が 13 のスレッドは、優先度が高いスレッドと見なされます。 この設定により、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スレッドには、他の多数のアプリケーションよりも高い優先度が与えられます。 したがって、通常、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スレッドは、実行可能な状態になると先に実行され、他のアプリケーションのスレッドからの割り込みを受けることはありません。 サーバーで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスだけが実行されていて他のアプリケーションが実行されていない場合は、この方法でパフォーマンスを向上させることができます。 ただし、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でメモリを集中的に消費する操作が発生した場合は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スレッドに割り込みをかけるのに十分な優先度が他のアプリケーションに与えられない可能性が高くなります。 

コンピューターで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の複数のインスタンスを実行していて、一部のインスタンスのみに対して priority boost を有効にしている場合、通常の優先度で実行されているすべてのインスタンスのパフォーマンスに悪影響を及ぼすことがあります。 また、priority boost が有効になっていると、サーバー上の他のアプリケーションやコンポーネントのパフォーマンスが低下することがあります。 したがって、このオプションは厳密に管理された条件下でのみ使用することをお勧めします。

## <a name="hot-add-cpu"></a>ホット アド CPU
ホット アド CPU とは、実行中のシステムに CPU を動的に追加する機能です。 CPU の追加は、物理的には新しいハードウェアの追加、論理的にはオンライン ハードウェア パーティション分割、仮想的には仮想化レイヤーの利用によって行われます。 [!INCLUDE[ssKatmai](../includes/ssKatmai-md.md)] 以降の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、ホット アド CPU をサポートしています。

ホット アド CPU の要件  
* ホット アド CPU をサポートするハードウェアが必要です。
* オペレーティング システムとして、Windows Server 2008 Datacenter の 64 ビット エディション、または Windows Server 2008 Enterprise Edition for Itanium-Based Systems が必要です。
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise が必要です。
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はソフト NUMA を使用するように構成することはできません。 ソフト NUMA の詳細については、「 [ソフト NUMA (SQL Server)](../database-engine/configure-windows/soft-numa-sql-server.md)」を参照してください。

CPU を追加しても、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で自動的にその CPU の使用が開始されることはありません。 これにより、別の目的で追加した CPU が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で使用されるのを防ぐことができます。 CPU の追加後に [RECONFIGURE](../t-sql/language-elements/reconfigure-transact-sql.md) ステートメントを実行して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が新しい CPU を使用可能なリソースとして認識するようにします。

> [!NOTE]
> [affinity64 mask](../database-engine/configure-windows/affinity64-mask-server-configuration-option.md) が構成されている場合、新しい CPU を使用するように affinity64 mask を変更する必要があります。
 
## <a name="best-practices-for-running-sql-server-on-computers-that-have-more-than-64-cpus"></a>64 基を超える CPU を搭載したコンピューター上で SQL Server を実行する場合のベスト プラクティス

### <a name="assigning-hardware-threads-with-cpus"></a>CPU へのハードウェア スレッドの割り当て
プロセッサを特定のスレッドにバインドするために、affinity mask および affinity64 mask サーバー構成オプションを使用しないでください。 これらのオプションは、64 基までの CPU に制限されます。 代わりに、 [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) の SET PROCESS AFFINITY オプションを使用してください。

### <a name="managing-the-transaction-log-file-size"></a>トランザクション ログ ファイル サイズの管理
トランザクション ログ ファイルのサイズの拡張に関して、自動拡張に依存しないでください。 トランザクション ログの拡張は、シリアルなプロセスである必要があります。 ログを拡張すると、ログの拡張が完了するまでトランザクションの書き込み操作が実行されなくなる場合があります。 ログ ファイルに対する領域をあらかじめ割り当てるには、その代わりに、環境における一般的なワークロードに十分に対応できる大きさの値にファイル サイズを設定します。

### <a name="setting-max-degree-of-parallelism-for-index-operations"></a>インデックス操作の並列処理の最大限度の設定
多数の CPU を搭載するコンピューター上では、一時的にデータベースの復旧モデルを一括ログ復旧モデルまたは単純復旧モデルに設定することで、インデックスの作成や再構築などのインデックス操作のパフォーマンスを向上させることができます。 これらのインデックス操作では、大量のログ アクティビティが生成されることがあるため、ログの競合によって、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が選択した最適な並列処理の程度 (DOP) に影響が及ぶおそれがあります。

また、これらの操作を行う場合は、**並列処理の最大限度 (MAXDOP: Max Degree Of Parallelism)** サーバー構成オプションの調整を検討してください。 次のガイドラインは、内部テストに基づき、一般的に推奨されます。 環境に最適な設定を決定するには、さまざまな MAXDOP 設定を試す必要があります。

* 完全復旧モデルでは、max degree of parallelism オプションの値を 8 以下に制限してください。   
* 一括ログ復旧モデルまたは単純復旧モデルでは、max degree of parallelism オプションを 8 より大きい値に設定することを検討してください。   
* NUMA が構成されているサーバーの場合、並列処理の最大限度は、それぞれの NUMA ノードに割り当てられている CPU 数を超える値に設定しないでください。 これは、クエリで 1 つの NUMA ノードのローカル メモリを使用する可能性が高く、それによりメモリのアクセス時間が改善される可能性があるためです。  
* 2009 年以前 (ハイパー スレッディング機能が改善される前) に製造されたサーバーでハイパー スレッディングが有効である場合、論理プロセッサではなく物理プロセッサ数を超える値を MAXDOP に設定しないでください。

並列処理の最大限度オプション詳細については、「[max degree of parallelism サーバー構成オプションの構成](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」をご覧ください。

### <a name="setting-the-maximum-number-of-worker-threads"></a>ワーカー スレッドの最大数の設定
ワーカー スレッドの最大数には、並列処理の最大限度の設定を超える値を必ず設定してください。 ワーカー スレッドの数は、サーバーに搭載されている CPU 数の 7 倍以上の数に設定する必要があります。 詳細については、 [max worker threads オプションの構成](../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)に関するページを参照してください。

### <a name="using-sql-trace-and-sql-server-profiler"></a>SQL トレースおよび SQL Server Profiler の使用
SQL トレースおよび SQL Profiler は、運用環境で使用しないことをお勧めします。 CPU 数が増えるに応じて、これらのツールの実行に伴うオーバーヘッドも大きくなります。 SQL トレースを運用環境で使用する必要がある場合は、トレース イベントの数を最小限にしてください。 負荷がある状態で各トレース イベントを慎重にプロファイリングおよびテストし、パフォーマンスに大きな影響を与えるイベントの組み合わせを使用しないように注意してください。

### <a name="setting-the-number-of-tempdb-data-files"></a>tempdb データ ファイルの数の設定
通常は、tempdb データ ファイルの数を CPU の数と一致させる必要があります。 ただし、tempdb のコンカレンシーの必要性を慎重に検討したうえで、データベース管理を減らすことができます。 たとえば、64 個の CPU が搭載されているシステムにおいて通常 tempdb を使用するクエリの数が 32 個に限られている場合、tempdb ファイルの数を 64 に増やしてもパフォーマンスは改善されません。

### <a name="sql-server-components-that-can-use-more-than-64-cpus"></a>64 基を超える CPU を使用できる SQL Server コンポーネント
次の表に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の各コンポーネントで 64 基を超える CPU を使用できるかどうかを示します。

|[処理名]   |実行可能なプログラム |64 個を超える CPU の使用 |  
|----------|----------|----------|  
|SQL Server データベース エンジン |Sqlserver.exe  |[ユーザー アカウント制御] |  
|Reporting Services |Rs.exe |いいえ |  
|Analysis Services  |As.exe |いいえ |  
|Integration Services   |Is.exe |いいえ |  
|Service Broker |Sb.exe |いいえ |  
|フルテキスト検索   |Fts.exe    |いいえ |  
|SQL Server エージェント   |Sqlagent.exe   |いいえ |  
|SQL Server Management Studio   |Ssms.exe   |いいえ |  
|SQL Server セットアップ   |Setup.exe  |いいえ |  
