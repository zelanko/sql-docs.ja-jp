---
title: Always On 可用性グループの SQL Server on Linux |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.openlocfilehash: 1273d445d52c00db01cac884b171e8feedceb49a
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206621"
---
# <a name="always-on-availability-groups-on-linux"></a>Always On Linux で可用性グループ

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux ベースの下の Always On 可用性グループ (Ag) の特性を記述します。[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]インストールします。 Linux と Windows Server フェールオーバー クラスター (WSFC) の違いについても説明-Ag のベースします。 参照してください、 [Windows ベースのドキュメント](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)Ag の基本については、同じ Windows および Linux を除く、WSFC で作業します。

可用性グループの高レベルの観点から[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]on Linux と同じ WSFC ベースの実装上にあります。 つまり、すべての制限と機能が同じですが、いくつかの例外。 主な相違点は次のとおりです。

-   Microsoft 分散トランザクション コーディネーター (DTC) は linux でサポートされていません[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]します。 アプリケーションが分散トランザクションの使用を求めたり、AG 必要がある場合は、デプロイ[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Windows にします。
-   Linux ベースの展開は、WSFC ではなく、Pacemaker を使用します。
-   Pacemaker には、ワークグループ クラスター シナリオを除く Windows での Ag のほとんどの構成とは異なり、Active Directory Domain Services (AD DS) ことが必要です。
-   1 つのノードから別の AG をフェールオーバーする方法は、Linux と Windows 間で異なります。
-   特定の設定など、`required_synchronized_secondaries_to_commit`のみ変更できますが、Linux 上の Pacemaker を使用して WSFC ベースのインストールは、TRANSACT-SQL を使用します。

## <a name="number-of-replicas-and-cluster-nodes"></a>レプリカとクラスター ノードの数

AG[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]合計 2 つのレプリカを持つことができます。 1 つのプライマリとセカンダリの可用性の目的でのみ使用できます。 読み取り可能なクエリなど、他の目的で使用できません。 AG[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]最大 9 つのレプリカを持つことができます。 同期は、プライマリと最大 8 つのセカンダリ、最大 3 つ (プライマリを含む) を 1 つ。 場合、基になるクラスターを使用することがあります合計 16 ノードの最大 Corosync が含まれている場合。 可用性グループが span と 16 のノードの最大 9[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]とに 2 つの[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]します。

」の説明に従って構成のみのレプリカを使用する必要が自動的に別のレプリカにフェールオーバーする機能を必要な 2 つのレプリカ構成[構成のみのレプリカとクォーラム](#configuration-only-replica-and-quorum)します。 構成のみのレプリカがで導入された[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]Cumulative Update 1 (CU1)、この構成で配置されている最小バージョン必要があるようにします。

Pacemaker を使用する場合にする必要があります適切に構成するため、稼働してままになります。 つまり、あるクォーラムと STONITH 必要が適切に実装する Pacemaker の観点から、他にも、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]構成専用レプリカなどの要件。

読み取り可能なセカンダリ レプリカでのみサポート[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]します。

## <a name="cluster-type-and-failover-mode"></a>クラスターの種類とフェールオーバー モード

初めて使用する[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]Ag のクラスターの種類の導入です。 Linux の場合は、2 つの有効な値があります。External と None です。 外部のクラスターの種類は、可用性グループの下に Pacemaker を使用することを意味します。 外部を使用してクラスターの種類は、フェールオーバー モードが外部にも設定する必要があります (新[!INCLUDE[sssql17-md](../includes/sssql17-md.md)])。 自動フェールオーバーがサポートされていますが、Pacemaker を使用する場合は、フェールオーバー モードを自動ではありません、外部に設定するよう、WSFC とは異なり。 WSFC の場合とは異なり、可用性グループを構成した後、可用性グループの Pacemaker 部分が作成されます。

None のクラスターの種類は、要件がないことは、可用性グループを使用して、Pacemaker を意味します。 Pacemaker が構成されているサーバー上であっても、可用性グループがある場合、None のクラスターの種類で構成されている Pacemaker をしないを参照してくださいまたはその AG を管理します。 None のクラスターの種類には、プライマリからセカンダリ レプリカへの手動フェールオーバーのみサポートされます。 なしで作成した AG は主に読み取りスケール アウト シナリオとアップグレードの対象とします。 ディザスター リカバリーまたは自動フェールオーバーが必要なローカルの可用性のようなシナリオで使用する、中には推奨されません。 リスナー ストーリー Pacemaker せずより複雑です。

クラスターの種類が格納されている、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]動的管理ビュー (DMV) `sys.availability_groups`、列の`cluster_type`と`cluster_type_desc`します。

## <a name="requiredsynchronizedsecondariestocommit"></a>必要な\_同期\_セカンダリ\_に\_コミット

初めて使用する[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]と呼ばれる Ag で使用される設定は、`required_synchronized_secondaries_to_commit`します。 これは、可用性グループに、現在プライマリである必要がありますセカンダリ レプリカの数を指示します。 これにより、自動フェールオーバー (外部のクラスターの種類で Pacemaker と統合) の場合のみなどと適切な数のセカンダリ レプリカがオンラインまたはオフラインの場合は、プライマリの可用性などの動作を制御します。 このしくみの詳細については、[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)を参照してください。 `required_synchronized_secondaries_to_commit`値が既定で設定され、Pacemaker によって管理される/[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 この値を手動で上書きすることができます。

組み合わせ`required_synchronized_secondaries_to_commit`と新しいシーケンス番号 (に格納されている`sys.availability_groups`) Pacemaker 通知と[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]など、自動フェールオーバーの発生、します。 その場合は、セカンダリ レプリカでは、最新の構成情報がすべて最新であることを意味、プライマリと同じシーケンス番号があります。

に対して設定できる 3 つの値がある`required_synchronized_secondaries_to_commit`:0、1、2 のいずれか。 これらは、レプリカが使用できなくなったときの動作の動作を制御します。 数値は、プライマリと同期する必要がありますセカンダリ レプリカの数に対応します。 動作は、Linux のとおりです。

-   0 - 自動フェールオーバーはありませんので、セカンダリ レプリカを同期する必要はありません。 プライマリ データベースは、常に使用できます。
-   1-1 つのセカンダリ レプリカは、プライマリと同期された状態である必要があります。自動フェールオーバーは、可能性があります。 セカンダリ同期レプリカが利用可能になるまで、プライマリ データベースは使用できません。
-   2-両方のセカンダリ レプリカを 3 つ以上のノードの AG の構成では、プライマリと同期する必要があります。自動フェールオーバーは、可能性があります。

`required_synchronized_secondaries_to_commit` だけでなくの同期レプリカですがデータの損失とフェールオーバーの動作を制御します。 1 または 2 の値を含むため、データの冗長性が必ずセカンダリ レプリカが同期される必要な常に。 データの損失がありません。

値を変更する`required_synchronized_secondaries_to_commit`、次の構文を使用します。

>[!NOTE]
>値を変更すると、リソースを再起動して、つまり短時間停止。 この問題を回避する唯一の方法で管理されないクラスター一時的にリソースを設定します。

**Red Hat Enterprise Linux (RHEL) および Ubuntu**

```bash
sudo pcs resource update <AGResourceName> required_synchronized_secondaries_to_commit=<Value>
```

**SUSE Linux Enterprise Server (SLES)**

```bash
sudo crm resource param ms-<AGResourceName> set required_synchronized_secondaries_to_commit <value>
```

場所*AGResourceName* 、AG 用に構成されたリソースの名前を指定し、*値*は 0、1、または 2。 パラメーターを管理する Pacemaker の既定値に設定するとをするには、値のない同じステートメントを実行します。

AG の自動フェールオーバーは、次の条件が満たされたときにできます。

-   プライマリ レプリカとセカンダリ レプリカは、同期データ移動に設定されます。
-   セカンダリには、同期 (同期していない)、つまり、同じデータ ポイントは、2 つの状態があります。
-   クラスターの種類は、外部に設定されます。 自動フェールオーバーが None のクラスターの種類ではできません。
-   `sequence_number`になるセカンダリ レプリカのプライマリには最大のシーケンス番号 - つまり、セカンダリ レプリカの`sequence_number`元のプライマリ レプリカから 1 つに一致します。

これらの条件が満たされており、プライマリ レプリカをホストするサーバーが失敗した場合は、AG では、同期レプリカに所有権が変更されます。 同期レプリカの動作 (存在できる 3 つの合計: 1 つのプライマリ レプリカと 2 つのセカンダリ レプリカ) でさらに制御できる`required_synchronized_secondaries_to_commit`します。 これにより、Windows と Linux の両方で、Ag で機能しますが完全に異なる方法で構成されています。 Linux では、値は AG リソース自体のクラスターで自動的に構成します。

## <a name="configuration-only-replica-and-quorum"></a>構成のみのレプリカとクォーラム

新しいも[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]CU1 の時点では構成専用レプリカ。 Pacemaker は、WSFC とは異なるため、クォーラム STONITH を必要とするときに特に 2 つのノード構成だけは機能しません、AG に。 Fci の場合、クォーラム メカニズム Pacemaker によって提供されるがあります。 問題ありませんが、クラスターの層ですべての FCI フェールオーバー調停が行われるためです。 AG の Linux での調停が行われます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]すべてのメタデータが格納されます。 これは構成専用レプリカが関係します。

それ以外の質問せず 3 番目のノードと同期されるレプリカの少なくとも 1 つ必要になります。 これには動作しません[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]、2 つのレプリカを AG に参加していることがあるできますのみであるためです。 構成のみのレプリカは、AG 構成の他のレプリカと同じで、master データベースで AG 構成を格納します。 構成のみのレプリカの可用性グループに参加しているユーザー データベースではありません。 構成データは、プライマリから同期的に送信されます。 この構成データは、自動または手動でかどうか、フェールオーバー時に使用されます。

クォーラムを維持し、外部のクラスターの種類で自動フェールオーバーを有効にする可用性グループは、そのいずれかの必要があります。

-   3 つの同期レプリカ ([!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]のみ) または。
-   構成のみのレプリカと 2 つのレプリカ (プライマリおよびセカンダリ) があります。

外部を使用しているかどうか、手動フェールオーバーが発生することができます、または None のクラスターの AG 構成の種類。 持つクラスターの種類が None の可用性グループの構成専用レプリカを構成することができます、しないで、展開が複雑になるためです。 これらの構成を手動で変更`required_synchronized_secondaries_to_commit`を少なくとも 1 つの同期レプリカがあるように、1 以上の値になります。

任意のエディションの構成専用レプリカをホストできる[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]など、[!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]します。 これは、ライセンス コストを最小限に抑えられるし、Ag の連携により、[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]します。 これは、3 つ目のサーバーだけの最小限の仕様を満たす必要がありますに必要なことは意味[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]AG のユーザー トランザクションのトラフィックを受け取っていないためです。

構成のみのレプリカを使用する場合、次の動作があります。

-   既定では、`required_synchronized_secondaries_to_commit`は 0 に設定します。 これは、ことができますので手動で変更を 1 に必要な場合。
-   プライマリが失敗した場合と`required_synchronized_secondaries_to_commit`が 0 の場合、セカンダリ レプリカが新しいプライマリになるし、読み取りと書き込みの両方を使用できます。 値が 1 の場合は、自動フェールオーバーは発生しますが、その他のレプリカがオンラインになるまで新しいトランザクションを受け付けません。
-   セカンダリ レプリカが失敗した場合と`required_synchronized_secondaries_to_commit`0 は、プライマリ レプリカのトランザクションを受け付けるが (手動または自動) のデータもフェールオーバー可能な保護がない場合、プライマリは、この時点で失敗すると、セカンダリ レプリカは使用できません。
-   構成専用レプリカに失敗した場合、AG は通常、機能しますが、自動フェールオーバーを行うことはできません。
-   同期セカンダリ レプリカと、構成専用レプリカの両方が失敗した場合、プライマリがトランザクションを受け入れることはできず、なく、プライマリが失敗します。

CU1 が既知のバグを使用して生成される corosync.log ファイルでログ記録`mssql-server-ha`します。 現在のメッセージと表示されます"1 つのシーケンス番号を受信することには 2 のみ受信されますセカンダリ レプリカで使用可能な必要なレプリカの数により、プライマリになることがない場合。 十分なレプリカが online に安全に、ローカル レプリカを昇格します。" 数値を元に戻す必要があります、およびと"2 つのシーケンス番号を受信することが 1 のみ受信されます。 十分なレプリカが online に安全に、ローカル レプリカを昇格します。" 

## <a name="multiple-availability-groups"></a>複数の可用性グループ 

Pacemaker クラスターまたは一連のサーバーあたり 1 つ以上の可用性グループを作成できます。 唯一の制限は、システム リソースです。 可用性グループの所有権は、マスターで表示されます。 別の Ag を別々 のノードによって所有できます。同じノードが実行されている、それらをすべてではなく必要があります。

## <a name="drive-and-folder-location-for-databases"></a>データベースのドライブとフォルダーの場所

Windows ベースの Ag の AG に参加しているユーザー データベース、構造体のドライブとフォルダーと同じになります。 たとえば、ユーザーのデータベースが`/var/opt/mssql/userdata`サーバー B でサーバー A、その同じフォルダーが存在する必要があります唯一の例外は、セクションで記した[Windows ベースの可用性グループ、レプリカとの相互運用](#interoperability-with-windows-based-availability-groups-and-replicas)します。

## <a name="the-listener-under-linux"></a>Linux でリスナー

リスナーは、AG の省略可能な機能です。 アプリケーションとエンドユーザーが、データをホストするサーバーを把握する必要はありませんように単一のエントリ ポイント (プライマリ レプリカまたは読み取り専用セカンダリ レプリカに読み取り/書き込み) のすべての接続を提供します。 Wsfc、これは、ネットワーク名リソースと (必要な) 場合、AD DS に登録された後、IP リソースの組み合わせを DNS と。 可用性グループ リソース自体と組み合わせて、その抽象化を提供します。 リスナーの詳細については、[リスナー、クライアント接続、およびアプリケーションのフェールオーバー](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)を参照してください。

Linux でリスナーが異なる方法で構成されているが、その機能は同じです。 Pacemaker のネットワーク名リソースの概念がないも AD DS 以外のオブジェクトが作成されました。これは、任意のノードで実行できる Pacemaker で作成した IP アドレス リソースだけです。 「表示名」の dns リスナーの IP リソースに関連付けられているエントリを作成する必要があります。 リスナーの IP リソースはその可用性グループのプライマリ レプリカをホストするサーバー上でアクティブになります。

Pacemaker が使用され、リスナーに関連付けられている IP アドレス リソースが作成された場合があります短時間停止して、IP アドレスが 1 つのサーバーを停止して、その他の開始と自動または手動フェールオーバーでかどうか。 この抽象化、1 つの名前と IP アドレスの組み合わせを通じて提供されますが、障害はマスクしません。 アプリケーションは、ある種の機能を検出し、再接続することで、切断を処理できる必要があります。

ただし、DNS 名と IP アドレスの組み合わせは、まだ十分なセカンダリ レプリカの読み取り専用のルーティングなど、WSFC でリスナーを提供するすべての機能を提供します。 AG を構成するときに「リスナー」も構成する必要がで[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 これは、TRANSACT-SQL の構文と同様に、ウィザードで確認できます。 これを構成する Windows の場合と同じように機能する 2 つの方法はあります。

-   外部のクラスターの種類を含む AG での IP アドレスに関連付けられているで作成した「リスナー」 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Pacemaker で作成したリソースの IP アドレスを指定する必要があります。
-   None のクラスターの種類で作成された可用性グループ、プライマリ レプリカに関連付けられている IP アドレスを使用します。

アプリケーションから読み取り専用のルーティング要求などのコーディネーターを指定した IP アドレスに関連付けられているインスタンスになります。

## <a name="interoperability-with-windows-based-availability-groups-and-replicas"></a>Windows ベースの可用性グループ、レプリカとの相互運用 

External または WSFC である 1 つのクラスターの種類を持つ可用性グループには、クロス プラットフォームのレプリカを含めることはできません。 これは true かどうか、可用性グループが[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]または[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]します。 つまり基になるクラスターで従来の可用性グループ構成で、1 つのレプリカは、WSFC と Pacemaker を使った Linux 上の他のすることはできません。

AG が NONE のクラスターの種類では、そのレプリカのため、同じ AG で Linux および Windows ベースの両方のレプリカが存在でしたする OS の境界を越えることができます。 例は、プライマリ レプリカが Windows ベースの Linux ディストリビューションのいずれかが、セカンダリここで表示されます。

![ハイブリッドなし](./media/sql-server-linux-availability-group-overview/image1.png)

分散型 AG では、OS の境界を越えることができますも。 これらの構成方法など、外部の中で構成されているいずれかの規則によって基になる可用性がバインドされた Linux でのみが、WSFC を使用して、可用性グループに参加していることを構成する可能性があります。 次に例を示します。

![ハイブリッド Dist AG](./media/sql-server-linux-availability-group-overview/image2.png)

<!-- Distributed AGs are also supported for upgrades from [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] to [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. For more information on how to achieve this, see [the article "x"].

If using automatic seeding with a distributed availability group that crosses OSes, it can handle the differences in folder structure. How this works is described in [the documentation for automatic seeding].
-->
 
## <a name="next-steps"></a>次の手順
[SQL Server on Linux の可用性グループを構成します。](sql-server-linux-availability-group-configure-ha.md)

[SQL Server on Linux の読み取りスケール可用性グループを構成します。](sql-server-linux-availability-group-configure-rs.md)

[RHEL で可用性グループのクラスター リソースを追加します。](sql-server-linux-availability-group-cluster-rhel.md)

[SLES での可用性グループのクラスター リソースを追加します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu での可用性グループのクラスター リソースを追加します。](sql-server-linux-availability-group-cluster-ubuntu.md)

[クロス プラットフォームの可用性グループを構成します。](sql-server-linux-availability-group-cross-platform.md)

