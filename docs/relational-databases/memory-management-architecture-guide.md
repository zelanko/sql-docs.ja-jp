---
title: "メモリ管理アーキテクチャ ガイド | Microsoft Docs"
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- guide, memory management architecture
- memory management architecture guide
ms.assetid: 7b0d0988-a3d8-4c25-a276-c1bdba80d6d5
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d00e5c97e6c27f3fe40b2066b5e194b8011f6b1e
ms.lasthandoff: 04/11/2017

---
# <a name="memory-management-architecture-guide"></a>メモリ管理アーキテクチャ ガイド
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

## <a name="memory-architecture"></a>メモリ アーキテクチャ

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、メモリの確保と解放が必要に応じて動的に行われます。 通常、管理者が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に割り当てるメモリ量を指定する必要はありませんが、このオプションは一部の環境で必要になるのでまだ存在しています。

ディスクの読み書きはコンピューター操作の中でも特にリソースを消費するので、どのようなデータベース ソフトウェアでも、ディスク I/O を最小限に抑えることを主な設計目標としています。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、データベースから読み取ったページを保持するバッファー プールがメモリ内に構築されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のコードの大部分は、ディスクとバッファー プールの間の物理的な読み書きの回数が最も少なくなるように記述されています。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、次の 2 つの目標のバランスを取ることを目指しています。

* システム全体のメモリ不足を防ぐため、バッファー プールが大きくなりすぎないようにする。
* バッファー プールのサイズを最大にして、データベース ファイルの物理 I/O を最小限に抑える。


> [!NOTE]
> 負荷の高いシステムでは、実行に大量のメモリを必要とする大きなクエリが必要最低限のメモリ量を確保できず、メモリ リソースの待機中にタイムアウト エラーが発生することがあります。 これを解決するには、 [query wait オプション](../database-engine/configure-windows/configure-the-query-wait-server-configuration-option.md)の値を増やします。 並列クエリの場合は、 [max degree of parallelism オプション](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)の値を減らすことを検討してください。
 
> [!NOTE]
> メモリ不足で負荷の高いシステムでは、クエリ プランにマージ結合、並べ替え、およびビットマップを使用したクエリが含まれていると、クエリがビットマップに必要な最低限のメモリ量を確保できなかった場合に、ビットマップが削除されることがあります。 この動作がクエリのパフォーマンスに影響を与える場合があります。そのために並べ替え処理がメモリに収まらなくなったときに、tempdb データベース内の作業テーブルの使用率が増加し、tempdb データベースのサイズが大きくなります。 この問題を解決するには、物理メモリを追加するか、より実行速度の速い別のクエリ プランを使用するようにクエリをチューニングします。
 
### <a name="providing-the-maximum-amount-of-memory-to-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に対する最大メモリ容量の指定

AWE および Locked Pages in Memory 特権を使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジンに次の容量のメモリを指定できます。 (次の表には、現在利用できない 32 ビット バージョンの列が含まれています)。

| |32 ビット <sup>1</sup> |64 ビット
|-------|-------|-------| 
|コンベンショナル メモリ |すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション。 プロセス仮想アドレス空間制限まで: <br>- 2 GB<br>- 3 GB (/3 gb のブート パラメーターを使用する場合) <sup>2</sup> <br>- 4 GB (WOW64 の場合) <sup>3</sup> |すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション。 プロセス仮想アドレス空間制限まで: <br>- 7 TB (IA64 アーキテクチャを使用する場合) (IA64 は [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 以降ではサポートされません)<br>- オペレーティング システムの最大容量 (x64 アーキテクチャを使用する場合) <sup>4</sup>
|AWE メカニズム ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で 32 ビット プラットフォームのプロセス仮想アドレス空間制限を超えることを許可する) |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard、Enterprise、および Developer エディション : バッファー プールは、最大 64 GB のメモリにアクセスできます。|該当なし <sup>5</sup> |
|Lock Pages in Memory オペレーティング システム (OS) 特権 (物理メモリのロックを許可し、ロックされたメモリの OS ページングを回避する)<sup>6</sup> |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard、Enterprise、および Developer エディション : AWE メカニズムを使用する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロセスで必要です。 AWE メカニズムによって割り当てられたメモリは、ページ アウトできません。 <br> AWE を有効にせずにこの特権を許可しても、サーバーに対する影響はありません。 |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise および Developer エディション : オペレーティング システムのページングを回避するために推奨されます。 ワークロードによっては、パフォーマンス上の利点が得られる場合があります。 アクセス可能なメモリ量は、コンベンショナル メモリの場合と似ています。 |

<sup>1</sup> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]から続けて 32 ビット バージョンを利用することはできません。  
<sup>2</sup> /3gb は、オペレーティング システムのブート パラメーターです。 詳細については、MSDN ライブラリを参照してください。  
<sup>3</sup> WOW64 (Windows on Windows 64) は、32 ビットの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が 64 ビットのオペレーティング システムで実行される場合のモードです。  
<sup>4</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard Edition supports up to 128 GB. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition は、オペレーティング システムの最大容量の最大値をサポートします。  
<sup>5</sup> sp_configure awe enabled オプションは、64 ビットの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に存在しますが、無視されます。    
<sup>6</sup> Lock Pages in Memory (LPIM) 特権が許可されている (AWE サポートの場合は 32 ビット、AWE そのものでは 64 ビットで) 場合は、サーバーの最大メモリも設定することをお勧めします。

> [!NOTE]
> 32 ビット オペレーティング システム上では、古いバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行できます。 32 ビットのオペレーティング システム上で 4 ギガバイトを超えるメモリにアクセスするには、Address Windowing Extensions (AWE) がメモリを管理する必要があります。 これは、64 ビット オペレーティング システムで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行するときには必要ありません。 AWE の詳細については、 [2008 ドキュメントの「](https://msdn.microsoft.com/library/ms189334) プロセス アドレス空間 [」および「](https://msdn.microsoft.com/library/ms191481) 大規模データベースのメモリ管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 」をご覧ください。   


## <a name="dynamic-memory-management"></a>動的メモリ管理

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジンの既定のメモリ管理動作では、システムでメモリ不足を発生させることなく、必要な量のメモリを獲得します。 データベース エンジンでは、Microsoft Windows の Memory Notification API を使用してこれを実現しています。

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の仮想アドレス空間は、バッファー プールによって占有される領域とそれ以外の領域という 2 つの別個の領域に分割できます。 AWE メカニズムが有効になっている場合、バッファー プールは AWE でマップされたメモリに存在し、データベース ページに追加領域を提供します。 

バッファー プールは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のプライマリ メモリの割り当て元となります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロセス内にある COM オブジェクトなどの外部コンポーネントは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のメモリ管理機能に対応していないため、バッファー プールによって占有される仮想アドレス空間の外部のメモリを使用します。

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を起動すると、システムの物理メモリの量、サーバー スレッドの数、さまざまな起動パラメーターなど、数多くのパラメーターに基づいてバッファー プール用の仮想アドレス空間のサイズが計算されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、計算された量のプロセス仮想アドレス空間をバッファー プール用に予約しますが、現在の負荷に必要な量だけ物理メモリを獲得 (コミット) します。

インスタンスでは、ワークロードのサポートに必要なメモリを獲得し続けます。 多くのユーザーが接続してクエリを実行すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では要求に応じて追加の物理メモリを獲得します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスでは、max server memory の割当量に達するか、または Windows によって余分な空きメモリがなくなったことが示されるまで、物理メモリを獲得し続けます。獲得したメモリの量が min server memory 設定よりも多く、Windows によって空きメモリの不足が示されると、メモリが解放されます。

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスが動作しているコンピューター上で他のアプリケーションを起動すると、メモリを消費し、物理メモリの空き領域が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の目標よりも少なくなります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスでは、メモリの消費を調整します。 他のアプリケーションが停止され、使用可能なメモリが増えると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスはメモリ割り当てのサイズを大きくします。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、数 MB のメモリの解放および獲得を毎秒行うことができるため、メモリ割り当ての変更に迅速に対応できます。


## <a name="effects-of-min-and-max-server-memory"></a>最小および最大サーバー メモリの効果

min server memory および max server memory 構成オプションは、Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジンのバッファー プールが使用するメモリ容量の上限と下限を設定します。 バッファー プールは、min server memory に指定されたメモリ容量をすぐには獲得しません。 バッファー プールは、初期化に必要なメモリのみで起動します。 データベース エンジンのワークロードが増えるにしたがって、そのワークロードに対応するために必要なメモリを獲得し続けます。 バッファー プールは、min server memory で指定しされたメモリ容量に達するまでは獲得したメモリを解放しません。 メモリ容量が min server memory に達すると、バッファー プールは標準アルゴリズムを使用して、必要に応じてメモリ容量を獲得または解放します。 唯一の違いは、バッファー プールはそのメモリ割り当てを min server memory の値より少ないメモリ容量にはせず、max server memory の値より多いメモリ容量は獲得しないということです。

> [!NOTE]
> プロセスとしての[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、max server memory オプションで指定された容量を超えるメモリを獲得します。 内部コンポーネントも外部コンポーネントも、バッファー プール外にメモリ容量を割り当てることができます。この場合は、メモリ容量が余分に消費されますが、通常、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]によって消費されるメモリ容量の最大部分は、バッファー プールに割り当てられたメモリ容量が占めます。


データベース エンジンが獲得するメモリ容量は、そのインスタンスのワークロードに完全に依存します。 あまり多くの要求を処理しない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスでは、まったく min server memory に達しないこともあります。

min server memory と max server memory の両方に同じ値を指定した場合、データベース エンジンに割り当てられたメモリがその値に達すると、データベース エンジンは動的なメモリの解放および獲得を停止します。

他のアプリケーションが頻繁に停止または起動されるコンピューター上で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスが動作している場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスによるメモリの割り当てと解放により、他のアプリケーションの起動時間が遅くなることがあります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が、1 つのコンピューター上で動作している複数のサーバー アプリケーションのうちの 1 つであるときも、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に割り当てるメモリ量をシステム管理者が制御しなければならない場合があります。 このような場合には、min server memory オプションと max server memory オプションを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が使用するメモリ量を制御できます。 詳細については、 [サーバー メモリ構成オプション](../database-engine/configure-windows/server-memory-server-configuration-options.md)の設定を参照してください。

min server memory および max server memory は MB 単位で指定されます。

## <a name="memory-used-by-includessnoversionincludesssnoversion-mdmd-objects-specifications"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの仕様で使用されるメモリ

次の一覧で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の各オブジェクトによって使用されるおおよそのメモリ量について説明します。 表示されている金額は概算であり、環境とオブジェクトの作成方法によって異なります。

* ロック: 64 バイト + (32 バイト * 所有者数)   
* ユーザー接続: 約 (3* *network_packet_size + 94 kb)    

ネットワーク パケット サイズは、アプリケーションと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジン間の通信に使用される表形式のデータ スキーム (TDS) パケットのサイズです。 既定のパケット サイズは 4 KB であり、network packet size 構成オプションによって制御されます。

複数のアクティブな結果セット (MARS) が有効になっている場合、ユーザー接続で使用されるメモリは約 (3 + 3 * num_logical_connections) * network_packet_size + 94 KB です。

## <a name="buffer-management"></a>バッファー管理

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースの主な目的はデータの格納と取得であるため、データベース エンジンの主要な特性は頻繁なディスク I/O ということになります。 ディスク I/O 操作は多くのリソースを消費するうえ、完了するのに比較的長い時間がかかるので、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では I/O の効率を上げることに重点を置いています。 バッファー管理は、この効率向上を実現するための重要なコンポーネントです。 バッファー管理コンポーネントは 2 つのメカニズムから構成されています。1 つはデータベース ページに対するアクセスと更新を行うバッファー マネージャーで、もう 1 つはデータベース ファイルの I/O を削減するバッファー キャッシュ (バッファー プール) です。 

### <a name="how-buffer-management-works"></a>バッファー管理のしくみ

バッファーはメモリ内の 8 KB のページで、データ ページやインデックス ページと同じサイズです。 したがって、バッファー キャッシュは 8 KB 単位のページに分割されます。 バッファー マネージャーは、データベース ディスク ファイルのデータ ページやインデックス ページをバッファー キャッシュに読み取って、変更されたページをディスクに書き戻すための機能を管理しています。 バッファー マネージャーが別のデータを読み取るためのバッファー領域を必要とするまで、そのページはバッファー キャッシュ内に残ります。 データに変更が加えられた場合だけ、そのデータがディスクに書き戻されます。 バッファー キャッシュ内のデータは、ディスクに書き戻す前に何度でも変更できます。 詳細については、「 [ページの読み取り](../relational-databases/reading-pages.md) 」および「 [ページの書き込み](../relational-databases/writing-pages.md)」をご覧ください。

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を起動すると、システムの物理メモリの量、構成されるサーバー スレッドの最大数、さまざまな起動パラメーターなど、数多くのパラメーターに基づいてバッファー キャッシュ用の仮想アドレス空間のサイズが計算されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、この計算された量のプロセス仮想アドレス空間 (メモリ ターゲット) をバッファー キャッシュ用に予約しますが、現在の負荷に必要な量だけ物理メモリを獲得 (コミット) します。 **sys.dm_os_sys_info** カタログ ビューの **bpool_commit_target** 列と [bpool_committed](../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) 列に対してクエリを実行すると、メモリ ターゲットとして予約されているページ数と、バッファー キャッシュ内で現在コミットされているページ数をそれぞれ返すことができます。

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の起動からバッファー キャッシュがメモリ ターゲットを取得するまでの間隔を、割り当て増加といいます。 この間、読み取り要求によって、必要に応じてバッファーが使用されます。 たとえば、1 ページの読み取り要求では、1 つのバッファー ページが使用されます。 つまり、割り当て増加は、クライアント要求の数や種類によって異なります。 1 ページずつの読み取り要求を 8 ページ分の要求にまとめて変換することで、割り当て増加を高速化しています。 これにより、特に多くのメモリが搭載されたコンピューターでは、割り当て増加が非常に高速に完了します。

バッファー マネージャーはほとんどのメモリを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロセスで使用するので、メモリ マネージャーと連携して他のコンポーネントでバッファーを使用できるようにします。 バッファー マネージャーは主に次のコンポーネントと対話します。

* リソース マネージャー。全体的なメモリ使用量を制御します。32 ビット プラットフォームではアドレス空間の使用量を制御します。  
* データベース マネージャーおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オペレーティング システム (SQLOS)。低レベルのファイル I/O 操作を行います。  
* ログ マネージャー。先行書き込みログ記録を行います。  

### <a name="supported-features"></a>サポートされている機能

バッファー マネージャーは、次の機能をサポートしています。

* NUMA (non-uniform memory access) に対応しています。 バッファー キャッシュ ページはハードウェア NUMA ノード間に分散されます。そのため、スレッドは外部メモリからではなく、ローカルの NUMA ノードに割り当てられているバッファー ページにアクセスすることができます。 
* ホット アド メモリをサポートしています。そのため、ユーザーはサーバーを再起動することなく物理メモリを追加できます。 
* 64 ビット プラットフォームの大きなページをサポートしています。 ページのサイズは、Windows のバージョンに固有です。 
* バッファー マネージャーは、動的管理ビューによって公開される追加の診断情報を提供します。 これらのビューを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に固有のさまざまなオペレーティング システム リソースを監視できます。 たとえば、sys.dm_os_buffer_descriptors ビューを使用すると、バッファー キャッシュ内のページを監視できます。   

### <a name="disk-io"></a>ディスク I/O
バッファー マネージャーはデータベースの読み取りと書き込みだけを行います。 他のファイル操作やデータベース操作 (開く、閉じる、拡張、圧縮など) は、データベース マネージャー コンポーネントおよびファイル マネージャー コンポーネントによって実行されます。 

バッファー マネージャーによるディスク I/O 操作には、次の特性があります。

* すべての I/O は非同期で実行されます。つまり、呼び出し側スレッドでの処理中でも、I/O 操作はバックグラウンドで進行します。
* すべての I/O は affinity I/O mask オプションが使用中でなければ、呼び出し側スレッドで発行されます。 affinity I/O mask オプションでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のディスク I/O が、指定した CPU のサブセットに関連付けられます。 ハイエンドな [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン トランザクション処理 (OLTP) 環境では、この拡張機能により、I/O を発行する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スレッドのパフォーマンスを向上できます。
* 複数ページの I/O は、スキャッター/ギャザー I/O を使用して実行されます。スキャッター/ギャザー I/O を使用すると、連続しないメモリ領域との間でデータを転送できます。 つまり、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、複数の物理 I/O 要求を回避しながら、バッファー キャッシュをすばやく使用またはフラッシュできます。 

#### <a name="long-io-requests"></a>実行時間の長い I/O 要求  
バッファー マネージャーは未処理状態が 15 秒以上続いた I/O 要求を報告します。 これはシステム管理者が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の問題か I/O サブシステムの問題かを区別するのに役立ちます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエラー ログには、次のようなエラー メッセージ 833 が報告および記録されます。

`` 
SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database [%ls] (%d). The OS file handle is 0x%p. The offset of the latest long I/O is: %#016I64x.
`` 

実行時間の長い I/O は読み取りまたは書き込みのどちらかの処理ですが、どちらの処理なのかはメッセージに示されません。 実行時間の長い I/O のメッセージは、警告であってエラーではありません。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に関する問題を示すものではありません。 これらのメッセージが報告されることにより、システム管理者は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の応答時間が遅い原因を追求したり、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の制御の範囲外にある問題を見分けたりするのに役立てることができます。 このように、メッセージに対するアクションは不要ですが、システム管理者は I/O 要求が長時間かかっている理由や、かかっている時間が正当であるかどうかを調べる必要があります。

#### <a name="causes-of-long-io-requests"></a>実行時間の長い I/O 要求の原因  
実行時間の長い I/O のメッセージは、I/O が永続的にブロックされていて決して完了しないこと (ロスト I/O ともいいます) を示す場合があります。また、I/O が単純にまだ完了していないことを示す場合があります。 この場合、どちらのシナリオなのかをメッセージから区別することはできません。ただ、ロスト I/O の結果、ラッチ タイムアウトが生じることがよくあります。

多くの場合、実行時間の長い I/O は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のワークロードによってディスク サブシステムに過度の負荷がかかっていることを示します。 ディスク サブシステムが不十分だと、次の現象が発生することがあります。

* 負荷の高い [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ワークロード中に、実行時間の長い I/O のメッセージがエラー ログに複数記録される。
* パフォーマンス カウンターに、長時間ディスクが遅延している、長時間ディスク キューに登録されている、ディスクのアイドル時間がないといった情報が表示される。  

実行時間の長い I/O は、I/O パス内のコンポーネント (ドライバー、コントローラー、ファームウェアなど) が原因になっている場合もあります。ディスク ヘッドの現在位置の近くにある新しい I/O 要求の処理を優先して、古い I/O 要求の処理を絶えず延期するためです。 読み取り/書き込みヘッドの現在位置の最も近くにある要求を優先して要求を処理する一般的な技法を、"エレベーター シーク" といいます。 これは Windows システム モニター (PERFMON.EXE) ツールと連携させるのが困難である場合があります。大半の I/O は速やかに処理されるためです。 実行時間の長い I/O 要求は大容量のシーケンシャル I/O を実行するワークロードによって増大することがあります。たとえば、バックアップおよび復元、テーブル スキャン、並べ替え、インデックスの作成、一括読み込み、ファイルの占有領域の解放処理などがあります。

実行時間の長い I/O のうち、以前の状態には関係ないと考えられる孤立した I/O は、ハードウェアやドライバーの問題が原因になっている場合があります。 システム イベント ログには、問題の診断に役立つ関連イベントが含まれていることがあります。

#### <a name="error-detection"></a>エラー検出  
データベース ページで 2 つのオプションのメカニズム (破損ページ保護とチェックサム保護) を使用して、ページがディスクに書き込まれてから再び読み取られるまでの間、ページの整合性を保証できます。 これらのメカニズムによって、データ ストレージだけでなく、ハードウェア コンポーネント (コントローラー、ドライバー、ケーブルなど)、およびオペレーティング システムに至るまで、個々の正確性を検証するための独立した手段が可能になります。 この保護はディスクに書き込む直前にページに追加され、ディスクから読み取られた後で検証されます。

#### <a name="torn-page-protection"></a>破損ページ保護  
破損ページ保護は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 で導入されたもので、主に電源障害によるページ破損を検出する方法です。 たとえば、予期しない電源障害でページの一部だけがディスクに書き込まれた状態になったとします。 破損ページ保護を使用すると、ページの 512 バイトの各セクター末尾に 2 ビットの署名が配置されます (その 2 ビットの元の内容は、署名の配置前にページ ヘッダーにコピーされます)。 書き込みが行われるたびに署名としてバイナリの 01 と 10 が交互に設定されるので、セクターの一部だけがディスクに書き込まれたときを常に判別することが可能です。つまり、後でページが読み取られたときにビットの正しくない状態の場合、ページが不適切に書き込まれたので、破損ページが検出されます。 破損ページ検出で使用されるリソースは最小限です。ただし、ディスクのハードウェア障害が原因で発生したすべてのエラーを検出できるわけではありません。

#### <a name="checksum-protection"></a>チェックサム保護  
チェックサム保護は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 から導入されたもので、今まで以上に強力なデータ整合性チェックを提供します。 チェックサムは各ページに書き込まれるデータから算出され、ページ ヘッダーに書き込まれます。 ページにチェックサムが書き込まれている場合は、そのページをディスクから読み取るたびにデータのチェックサムが再計算されます。そして、新しく計算されたチェックサムと、現在書き込まれているチェックサムが異なる場合は、エラー 824 が生成されます。 チェックサム保護はページの各バイトの影響を受けるので、破損ページ保護よりも多くのエラーをキャッチできますが、使用されるリソースがやや多くなります。 チェックサムが有効になっている場合、電源障害、欠陥のあるハードウェアやソフトウェアが原因で発生するエラーは、バッファー マネージャーがディスクからページを読み取るたびに検出できます。

使用されている種類のページ保護は、ページが含まれているデータベースの属性です。 チェックサム保護は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 以降で作成されたデータベースの既定の保護です。 ページ保護のメカニズムはデータベースの作成時に指定するもので、ALTER DATABASE を使用して変更できます。 ページ保護の現在の設定を確認するには、 [sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの page_verify_option 列、または [DATABASEPROPERTYEX](../t-sql/functions/databasepropertyex-transact-sql.md) 関数の IsTornPageDetectionEnabled プロパティを照会します。 ページ保護の設定が変更されたとき、新しい設定がデータベース全体にすぐに反映されるわけではありません。 個々のページの出力時に、現在のデータベースの保護レベルがそのページに適用されます。 つまり、データベースはそれぞれ保護の種類が異なるページで構成されている場合があります。 

## <a name="understanding-non-uniform-memory-access"></a>Non-Uniform Memory Access について

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、Non-Uniform Memory Access (NUMA) に対応しているので、特殊な構成を行わなくても NUMA ハードウェアで適切に実行されます。 プロセッサのクロック速度や数が増加するにつれて処理能力が向上しますが、その一方で、向上した能力の活用に必要となるメモリの待機時間を減らすことが困難になります。 ハードウェア ベンダーはメモリの待機時間をなくすために、大容量の L3 キャッシュを搭載していますが、この解決策にも限界があります。 この問題に対する、拡張性に優れた解決方法が NUMA アーキテクチャです。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、アプリケーションを変更しなくても NUMA ベースのコンピューターを活用できるように設計されています。 詳細については、「 [ソフト NUMA を使用するように SQL Server を構成する方法](../database-engine/configure-windows/soft-numa-sql-server.md)」をご覧ください。

## <a name="see-also"></a>参照
[ページの読み取り](../relational-databases/reading-pages.md)   
 [ページの書き込み](../relational-databases/writing-pages.md)


