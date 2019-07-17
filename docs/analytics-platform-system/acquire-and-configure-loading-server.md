---
title: 取得し、Parallel Data Warehouse の読み込みサーバーの構成 |Microsoft Docs
description: この記事では、取得、および読み込みサーバー データの読み込みを並列データ ウェアハウス (PDW) を送信するための非アプライアンス Windows システムとして構成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d753237841695786de3d368bebf9a606875ea634
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961618"
---
# <a name="acquire-and-configure-a-loading-server-for-parallel-data-warehouse"></a>取得し、Parallel Data Warehouse の読み込みサーバーの構成
この記事では、取得、および読み込みサーバー データの読み込みを並列データ ウェアハウス (PDW) を送信するための非アプライアンス Windows システムとして構成する方法について説明します。  
  
## <a name="Basics"></a>基本  
読み込みサーバーの場合:  
  
-   1 つのサーバーにすることはありません。 複数のサーバーの読み込みと同時に読み込めます。  
  
-   提供され、IT チームによって管理されています。 サーバーまたは PDW にデータを読み込むために使用できるサーバーが既にある可能性があります。  
  
-   非アプライアンス ラックにあるし、Analytics Platform System appliance 内に配置することはできません。  
  
-   アプライアンスの InfiniBand ネットワーク経由またはイーサネット経由でアプライアンスに接続されます。 パフォーマンス、InfiniBand を使用してをお勧めします。  
  
-   アプライアンスのドメインではなく、独自の顧客ドメインです。 顧客のドメインとアプライアンスのドメインと信頼関係はありません。  
  
## <a name="Step1"></a>手順 1:容量要件を決定します。  
同時読み込みを実行する 1 つまたは複数の読み込みサーバー システムの読み込みを設計できます。 読み込みの各サーバーをワークロードのパフォーマンスとストレージの要件を処理する限り、専用の読み込み、のみにする必要はありません。  
  
読み込みサーバーのシステム要件は、独自のワークロードにほぼ完全に依存します。 使用して、[サーバー容量計画ワークシートの読み込み](loading-server-capacity-planning-worksheet.md)容量の要件を確認するためです。  
  
## <a name="Step2"></a>手順 2:サーバを取得します。  
これで、容量の要件をより深く理解するには、サーバーとのネットワーク コンポーネントを購入またはプロビジョニングする必要がありますを計画できます。 次の要件の一覧を購入の計画に組み込むと、サーバーを購入するか、既存のサーバーをプロビジョニングします。  
  
### <a name="R"></a>ソフトウェアの要件  
サポートされるオペレーティング システム:  
  
-   Windows Server 2012 または Windows Server 2012 R2。 これらのオペレーティング システムでは、FDR のネットワーク アダプターが必要です。  
  
-   Windows Server 2008 R2. この OS では、DDR のネットワーク アダプターが必要です。  
  
サーバーは、dwloader のコマンドライン読み込みツールを使用するには、EN-US ロケールを使用する必要があります。 dwloader は、その他のロケールをサポートしていません。  
  
### <a name="networking-requirements-for-windows-server-2012-and-windows-server-2012-r2"></a>Windows Server 2012 および Windows Server 2012 R2 のネットワーク要件  
読み込みは必要ありません、InfiniBand はサーバーの読み込みの推奨される接続の種類です。 最適なパフォーマンス、読み込みサーバー アプライアンスの InfiniBand ネットワークを接続するのに Windows Server 2012 または Windows Server 2012 R2、および、FDR InfiniBand ネットワーク アダプターを使用します。  
  
Windows Server 2012 または Windows Server 2012 R2 の InfiniBand 接続を準備します。  
  
1.  計画、サーバーのラックを閉じて、アプライアンスに十分な InfiniBand スイッチ アプライアンスに接続することができます。 InfiniBand の Mellanox テクノロジの詳細については、ホワイト ペーパーを参照してください。 [InfiniBand 概要](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf)します。  
  
2.  Mellanox connectx-3 FDR InfiniBand シングルまたはデュアル ポートのネットワーク アダプターを購入します。 データ転送中にフォールト トレランスのための 2 つのポートを持つネットワーク アダプターを購入することをお勧めします。 2 つのポートのネットワーク アダプターが高可用性のために必要です。  
  
3.  デュアル ポート カードは、FDR InfiniBand 2 本のケーブルまたは 1 つのポートのカードの 1 の FDR InfiniBand ケーブルを購入します。 FDR InfiniBand ケーブルでは、読み込みのサーバーをアプライアンスの InfiniBand ネットワークに接続します。 ケーブルの長さは、環境に従ってに読み込み、サーバーとアプライアンスの InfiniBand スイッチ間の距離によって異なります。  
  
## <a name="Step3"></a>手順 3:サーバーの InfiniBand ネットワークに接続します。  
読み込みサーバーの InfiniBand ネットワークを接続するのにには、次の手順を使用します。 サーバーが、InfiniBand ネットワークを使用していない場合は、この手順をスキップします。  
  
1.  ラック、サーバーを閉じてアプライアンスに十分なために、アプライアンスの InfiniBand ネットワークに接続することができます。  
  
2.  読み込みサーバーに、InfiniBand Mellanox connectx-3 FDR InfiniBand ネットワーク アダプターをインストールします。  
  
3.  アプライアンスの最初のラック内の 2 つの InfiniBand スイッチの 1 つに、InfiniBand ネットワーク アダプターを接続するのにには、FDR ケーブルを使用します。  
  
4.  インストールし、InfiniBand ネットワーク アダプターの適切な Windows ドライバーを構成します。  
  
    -   Windows 用の InfiniBand ドライバーは、OpenFabrics Alliance、InfiniBand ベンダーに業界コンソーシアムによって開発されています。  適切なドライバーは、InfiniBand ネットワーク アダプターに配布されたことがあります。 それ以外の場合は、ドライバーは www.openfabrics.org からダウンロードできます。  
  
5.  ネットワーク アダプターの InfiniBand と DNS の設定を構成します。 構成手順については、次を参照してください。[構成の InfiniBand ネットワーク アダプター](configure-infiniband-network-adapters.md)します。  
  
## <a name="Step4"></a>手順 4:読み込みツールをインストールします。  
クライアント ツールは、Microsoft ダウンロード センターからダウンロードできます。 

Dwloader をインストールするには、クライアント ツールから dwloader のインストールを実行します。
  
読み込みの Integration Services を使用する場合は、Integration Services と Integration Services の変換先アダプターをインストールする必要があります。 アダプターは、クライアント ツールで利用できます。

<!-- To install the des[Install Integration Services Destination Adapters](install-integration-services-destination-adapters.md). 
--> 
  
## <a name="Step5"></a>手順 5:読み込みを開始します。  
データの読み込みを開始する準備が整いました。 詳細については、以下をご覧ください。  
  
1.  [dwloader のコマンドライン読み込みツール](dwloader.md)  
  
2.  [負荷の概要](load-overview.md)  
  
## <a name="performance"></a>パフォーマンス  
読み込みの Windows Server 2012 以降のパフォーマンスを最適なオペレーティング システムが、ゼロで既存のデータを上書きされないデータが上書きされるように、ファイルの瞬時初期化でにします。 セキュリティ上のリスクは、以前のデータは、ディスクが存在するため、これは場合、ファイルの瞬時初期化をオフになります。  
  
## <a name="Security"></a>セキュリティ通知  
アプライアンス上に読み込むデータが保存されないため、IT チームは、データの読み込みをセキュリティのすべての側面を管理する責任を負います。 たとえば、読み込むデータのセキュリティ、負荷を格納するために使用するサーバーのセキュリティ、および読み込みサーバーを SQL Server PDW アプライアンスに接続するネットワーク インフラストラクチャのセキュリティの管理が含まれます。  
  
> [!IMPORTANT]  
> Dwloader のコマンドライン読み込みツールを使用する各読み込みサーバーのセキュリティ保護に特に重要ですが。 Dwloader のデータの読み込み、時にコントロールのノードで最初に認証し認証成功後に、データ読み込みサーバーからのコンピューティング ノードに直接データ チャネル上でします。 証明書の検証は、各読み込みサーバーと各コンピューティング ノード間で手シェイク中には発生しません。 これにより、読み込み中に各データ チャネルへの潜在的な中間の攻撃に対して公開されているコンピューティング ノードです。 これらの攻撃は、データの改ざんや情報の漏えいになる可能性があります。  
  
データのセキュリティ上のリスクを減らすために、次を勧め。  
  
-   PDW にデータを読み込むだけを目的に使用される 1 つの Windows アカウントを指定します。 このアカウントの読み込み場所、およびこれ以外の場所にアクセス許可を許可します。  
  
-   データを読み込むためのアクセス許可を持つ 1 つの PDW ユーザーを指定します。 セキュリティの要件に応じてデータベースごとの 1 つの特定ユーザーことができます。  
  
-   読み込みサーバーでの操作には、信頼されている内部ネットワークの外部からのデータをプルする元の UNC パスを使用できます。 ネットワーク上や名前解決に影響する機能により、攻撃者が傍受または SQL Server の PDW に送信されるデータを変更します。 これは、改ざんや情報漏えいのリスクを表示します。 接続で署名を要求することによって、改ざんを軽減する必要があります。 このリスクを軽減するで、次のグループ ポリシー オプションを設定します。**セキュリティ \ セキュリティ オプション**読み込みサーバー上。**Microsoft ネットワーク クライアント:常に通信にデジタル署名します。有効になっています。**  
  
-   ファイルの瞬時初期化では、Windows Server 2012 以降をオフにします。 これは、パフォーマンスのセクションで説明したように、パフォーマンスとセキュリティのトレードオフです。 セキュリティ ニーズに合わせて最適なものを決定する必要があります。  
  
## <a name="see-also"></a>参照  
[バックアップと復元の概要](backup-and-restore-overview.md)  
  
