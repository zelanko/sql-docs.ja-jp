---
title: Always On 可用性グループの SQL Server on Linux |Microsoft ドキュメント
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.openlocfilehash: b5716ab08f48900f80e24de46bc1b556884c7263
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="always-on-availability-groups-on-linux"></a>Always On Linux 上の可用性グループ

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Always On 可用性グループ (Ag) の下にある Linux ベースの特性を説明[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]インストールします。 Linux と Windows Server フェールオーバー クラスター (WSFC) の違いについても説明、Ag のベースします。 参照してください、 [Windows ベースのドキュメント](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)Ag の基本の Windows および、WSFC を除く Linux で作業と同じにします。

可用性グループの高レベルの観点から[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]on Linux は、同じ WSFC ベースの実装上にあります。 つまり、すべての制限事項と機能が同じである、いくつかの例外。 主な相違点は次のとおりです。

-   Linux の Microsoft 分散トランザクション コーディネーター (DTC) はサポートされていません[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]です。 展開の場合は、アプリケーションは、分散トランザクションの使用を要求して、AG 必要があります、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] windows です。
-   Linux ベースの展開は、WSFC ではなくペースを使用します。
-   ペースには、ワークグループのクラスターのシナリオを除く Windows 上の Ag のほとんどの構成とは異なり、Active Directory ドメイン サービス (AD DS) ことが必要です。
-   間には、1 つのノードから AG が失敗する方法は、Linux と Windows の間で異なります。
-   特定の設定など、`required_synchronized_secondaries_to_commit`のみ変更できますが、Linux 上のペースを使用して WSFC ベースのインストールは、TRANSACT-SQL を使用します。

## <a name="number-of-replicas-and-cluster-nodes"></a>レプリカおよびクラスター ノードの数

AG[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]合計 2 つのレプリカを持つことができます。 1 つのプライマリとセカンダリの可用性の目的でのみ使用できます。 読み取り可能なクエリなど、他の何らかの使用することはできません。 AG[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]合計最大 9 個のレプリカを持つことができます: プライマリと最大 8 つのセカンダリ、最大 3 つ (プライマリを含む) を 1 つは同期していることができます。 基になるクラスターを使用する場合があります合計 16 ノードの最大 Corosync が含まれている場合。 可用性グループが最大で 9 個と 16 個のノードにまたがることができます[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]が 2 つ[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]です。

」の説明に従って、レプリカの構成のみを使用する必要を自動的に別のレプリカにフェールオーバーする機能を必要とする 2 つのレプリカ構成[構成専用のレプリカとクォーラム](#configuration-only-replica-and-quorum)です。 構成専用のレプリカで導入された[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]Cumulative Update 1 (CU1) をこの構成で配置されている最小バージョンをする必要があるようにします。

ペースを使用する場合にする必要があります適切に構成するため、立ち上がっており実行中になります。 つまり、あるクォーラムと STONITH 実装する必要が正しくペースのパースペクティブから、他にも、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]構成専用レプリカなどの要件です。

読み取り可能なセカンダリ レプリカでのみサポート[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]です。

## <a name="cluster-type-and-failover-mode"></a>クラスターの種類とフェールオーバー モード

初めて使用する[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]Ag のクラスターの種類を導入します。 Linux では、次の 2 つの有効な値: 外部、none で調整します。 外部のクラスターの種類は、可用性グループの下にあるペースが使用されることを意味します。 外部を使用してクラスターの種類は、フェールオーバー モードが外部にも設定する必要があります (の新機能も[!INCLUDE[sssql17-md](../includes/sssql17-md.md)])。 自動フェールオーバーがサポートされているが、WSFC とは異なりフェールオーバー モードに設定されている外部、自動ではありません、ペースを使用する場合。 WSFC とは異なり、可用性グループを構成した後、可用性グループのペース部分が作成されます。

None のクラスターの種類は、こと、要件はありません。 また、AG、ペースを意味します。 ペースが構成されているサーバー上でも場合は、AG しなくても、クラスターの種類で構成されているペースをいないを参照してくださいまたはその可用性グループを管理します。 None のクラスターの種類には、セカンダリ レプリカにプライマリ サーバーからの手動フェールオーバーのみサポートしています。 なしで作成された、AG は、主に読み取りのスケール アウト シナリオとアップグレードの対象とします。 障害復旧など、自動フェールオーバーがないために必要なローカルの可用性のシナリオで使用する、中には推奨されません。 リスナーのストーリーはペースせずより複雑なもあります。

クラスターの種類に格納されている、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]動的管理ビュー (DMV) `sys.availability_groups`、列の`cluster_type`と`cluster_type_desc`です。

## <a name="requiredsynchronizedsecondariestocommit"></a>必要な\_同期\_セカンダリ\_に\_コミット

初めて使用する[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]と呼ばれる Ag によって使用される設定は、`required_synchronized_secondaries_to_commit`です。 これは、可用性グループに、プライマリと lockstep にする必要があるセカンダリ レプリカの数を示しています。 これにより、自動フェールオーバー (ペースの外部のクラスターのタイプと統合) の場合のみなどを有効にされ、セカンダリ レプリカの数が、オンラインまたはオフラインの場合は、プライマリの可用性などの動作を制御します。 このしくみの詳細については、次を参照してください。[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。 `required_synchronized_secondaries_to_commit`値が既定の設定し、ペースで保持されている/[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 この値を手動でオーバーライドすることができます。

組み合わせ`required_synchronized_secondaries_to_commit`と新しいシーケンス番号 (に格納されています`sys.availability_groups`) ペースを通知し、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]など、自動フェールオーバーが行われる、します。 その場合は、セカンダリ レプリカでは、最新のすべての構成情報を最新の状態は、プライマリと同じシーケンス番号があります。

設定できる 3 つの値がある`required_synchronized_secondaries_to_commit`: 0、1、または 2 です。 これらは、レプリカが使用できなくなった場合の動作の動作を制御します。 数値は、プライマリと同期する必要がありますセカンダリ レプリカの数に対応します。 動作は、Linux のとおりです。

-   0 – 自動フェールオーバーはない可能なセカンダリ レプリカを同期する必要がないためです。 プライマリ データベースは、常に使用できます。
-   1 – 1 つのセカンダリ レプリカがプライマリ; と同期済み状態にする必要があります。自動フェールオーバーが可能です。 同期セカンダリ レプリカが利用可能になるまで、プライマリ データベースは使用できません。
-   2 –; プライマリと 3 つ以上のノード AG の構成で両方のセカンダリ レプリカを同期する必要があります自動フェールオーバーが可能です。

`required_synchronized_secondaries_to_commit` だけでなくの同期レプリカですがデータの損失とフェールオーバーの動作を制御します。 1 または 2 の値にセカンダリ レプリカは常に必要同期するのには常にあるデータの冗長性。 データが失われるをのためなしです。

値を変更する`required_synchronized_secondaries_to_commit`、次の構文を使用します。

>[!NOTE]
>値を変更すると、リソースを再起動して、短時間停止を意味します。 この問題を回避する唯一の方法で管理されないクラスター一時的にリソースを設定します。

**Red Hat Enterprise Linux (RHEL) および Ubuntu**

```bash
sudo pcs resource update <AGResourceName> required_synchronized_secondaries_to_commit=<Value>
```

**SUSE Linux Enterprise Server (SLES)**

```bash
sudo crm resource param ms-<AGResourceName> set required_synchronized_secondaries_to_commit <value>
```

ここで*AGResourceName* 、可用性グループ用に構成されたリソースの名前を指定し、*値*は 0、1、または 2 です。 パラメーターを管理するペースの既定値に戻すには、それを設定するには、値のない同じのステートメントを実行します。

自動フェールオーバー、AG は、次の条件が満たされたときにできます。

-   プライマリ レプリカとセカンダリ レプリカは、同期のデータの移動に設定されます。
-   セカンダリには、同期されている (同期中にありません)、つまり、2 つは、同じデータ ポイントでの状態があります。
-   クラスターの種類は、外部に設定されます。 自動フェールオーバーのなしのクラスターのタイプはできません。
-   `sequence_number`になるセカンダリ レプリカのプライマリが最も高いシーケンス番号: つまり、セカンダリ レプリカの`sequence_number`元のプライマリ レプリカから 1 つに一致します。

これらの条件が満たされてし、失敗した場合、プライマリ レプリカをホストしているサーバー、AG は同期レプリカへの所有権を変更します。 同期レプリカの動作は、(存在できる 3 つの合計: 1 つのプライマリ レプリカと 2 つのセカンダリ レプリカ) でさらに制御できます`required_synchronized_secondaries_to_commit`です。 これにより、Windows と Linux の両方の Ag とでも動作しますが完全に異なる方法で構成されています。 Linux では、値は AG リソース自体に、クラスターによって自動的に構成します。

## <a name="configuration-only-replica-and-quorum"></a>構成専用のレプリカとクォーラム

新機能も[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]CU1 時点では、構成専用レプリカです。 ペースは異なるため、WSFC よりも、クォーラムと STONITH を必要とするときに特に 2 つのノードの構成のみは機能しません、AG になります。 FCI のペースで提供されるクォーラム メカニズムもかまいません、クラスターの層のすべての FCI フェールオーバー判別が行われるためです。 AG の Linux での判別が行われます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]すべてのメタデータが格納されます。 これは、活躍するが、構成のみのレプリカです。

せず何でも、3 番目のノードと、少なくとも 1 つの同期レプリカが必要になります。 これが使用できない[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]AG に参加している 2 つのレプリカにしか持てないため、します。 構成専用のレプリカは、AG の構成内の他のレプリカと同じで、master データベースは、AG の構成を格納します。 構成専用レプリカには、可用性グループに参加しているユーザー データベースがありません。 構成データは、プライマリから同期的に送信されます。 自動か手動かにかかわらず、この構成データは、フェールオーバー時に使用されます。

クォーラムを維持して、外部のクラスターの種類を自動フェールオーバーを有効にする可用性グループは、そのいずれかが必要です。

-   次の 3 つの同期レプリカがある ([!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]のみ) または。
-   2 つのレプリカ (プライマリとセカンダリ) だけでなく、レプリカの構成のみがあります。

AG 構成の種類をクラスター None または外部を使用するかどうか、手動フェールオーバーが発生することができます。 構成専用のレプリカは、none クラスター型を持つ可用性グループを構成できますが、これは推奨されません、展開が複雑になるため。 これらの構成を手動で変更`required_synchronized_secondaries_to_commit`に少なくとも 1 つの同期レプリカがあるように、1 以上の値を作成します。

任意のエディションの構成のみのレプリカをホストできる[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]など、[!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]です。 これは、ライセンス コストを最小限になりでの Ag と連携して[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]です。 つまり、3 番目のために必要のみサーバーの最低限の仕様を満たしている必要がある[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]可用性グループのユーザー トランザクション トラフィック受信していないため、します。

構成専用のレプリカを使用すると、次の動作があります。

-   既定では、`required_synchronized_secondaries_to_commit`は 0 に設定します。 これは、手動で変更できますを 1 に必要な場合。
-   プライマリが失敗した場合と`required_synchronized_secondaries_to_commit`が 0 の場合、セカンダリ レプリカが新しいプライマリとなるし、読み取りと書き込みの両方を使用できます。 値が 1 の場合は、自動フェールオーバーは発生しませんが、他のレプリカがオンラインになるまで新しいトランザクションを受け入れません。
-   セカンダリ レプリカが失敗した場合と`required_synchronized_secondaries_to_commit`0 は、プライマリ レプリカがまだトランザクションを受け入れるには、プライマリは、この時点で失敗した場合、データもフェールオーバーの保護を (手動または自動)、セカンダリ レプリカは使用できません。
-   構成専用のレプリカが失敗すると、AG は通常、機能しますが、自動フェールオーバーは実行されません。
-   同期セカンダリ レプリカと構成専用のレプリカの両方が失敗した場合、プライマリが、トランザクションを受け入れることはできず、先がない、プライマリに失敗します。

CU1 は、既知のバグを経由して生成される corosync.log ファイルでログ記録`mssql-server-ha`です。 セカンダリ レプリカが使用可能な必須のレプリカの数により、プライマリとなるできない場合は、現在というメッセージが表示"を 1 のシーケンス番号を受信しましたが、だけ受け取りました 2 です。 十分なレプリカが online に安全に、ローカル レプリカを昇格します。" 数値を元に戻す必要がありますと"を 2 つのシーケンス番号を受信しましたが、だけ受け取りました 1 です。 十分なレプリカが online に安全に、ローカル レプリカを昇格します。" 

## <a name="multiple-availability-groups"></a>複数の可用性グループ 

ペース クラスターまたは一連のサーバーあたり 1 つ以上の可用性グループを作成できます。 唯一の制限事項は、システム リソースです。 可用性グループの所有権は、マスターによって表示されます。 別の Ag を所有できるさまざまなノードです。同じノードで実行されている、それらをすべて必要があります。

## <a name="drive-and-folder-location-for-databases"></a>データベースのドライブとフォルダーの場所

Windows ベースの Ag のように、可用性グループに参加しているユーザー データベースのドライブおよびフォルダー構造が同等でなければなりません。 たとえば、ユーザーのデータベースが`/var/opt/mssql/userdata`サーバー A で同じフォルダーにはサーバー B で存在する必要があります唯一の例外が、セクションで説明した[Windows ベースの可用性グループ、レプリカとの相互運用](#interoperability-with-windows-based-availability-groups-and-replicas)です。

## <a name="the-listener-under-linux"></a>Linux で、リスナー

リスナーは、AG の省略可能な機能です。 アプリケーションとエンドユーザーが、データをホストするサーバーを知る必要はありませんように単一のエントリ ポイントをプライマリ レプリカまたは読み取り専用セカンダリ レプリカ (読み取り/書き込み) のすべての接続を提供します。 Wsfc では、これは、組み合わせ、ネットワーク名リソースと IP リソースは、(必要な場合)、AD DS に登録し、DNS とします。 可用性グループ リソース自体と組み合わせて、その抽象化を提供します。 リスナーの詳細については、次を参照してください。[リスナー、クライアント接続、およびアプリケーションのフェールオーバー](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)です。

Linux でリスナーが異なる方法で構成されているが、その機能は同じです。 ペース、内のネットワーク名リソースの概念がないもがオブジェクトを AD DS; の作成だけに IP アドレス リソースが任意のノードで実行できるペースで作成します。 「表示名」の dns リスナーの IP リソースに関連付けられているエントリを作成する必要があります。 リスナーの IP リソースのみ、その可用性グループのプライマリ レプリカをホストするサーバー上でアクティブになります。

ペースが使用され、IP アドレス リソースが作成したリスナーに関連付けられている場合があります短時間停止、IP アドレスが、1 つのサーバーを停止して、別の開始と自動または手動フェールオーバーであるかどうか。 これにより、1 つの名前と IP アドレスの組み合わせによって抽象化中、停止はマスクしません。 アプリケーションは、これを検出し、再接続する機能のいくつかの並べ替え用意することによって切断を処理できる必要があります。

ただし、DNS 名と IP アドレスの組み合わせがまだ十分なセカンダリ レプリカに対する読み取り専用ルーティングなどの WSFC でリスナーを提供するすべての機能を提供します。 構成すると、AG、「リスナー」する必要があるで構成する[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 これは、TRANSACT-SQL の構文と同様に、ウィザードで確認できます。 これにはこの構成できることを Windows 上と同じように機能する 2 つの方法があります。

-   作成した「リスナー」に外部のクラスターの種類と、AG の IP アドレスが関連付けられている[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ペースで作成されたリソースの IP アドレスを指定する必要があります。
-   None のクラスターの種類で作成された、AG のプライマリ レプリカに関連付けられている IP アドレスを使用します。

指定された IP アドレスに関連付けられているインスタンスでは、アプリケーションからの読み取り専用ルーティング要求などのコーディネーターになります。

## <a name="interoperability-with-windows-based-availability-groups-and-replicas"></a>Windows ベースの可用性グループ、レプリカとの相互運用 

クロス プラットフォームそのレプリカ、AG の外部または WSFC クラスターの型を持つことはできません。 これは true かどうか、可用性グループが[!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]または[!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]です。 つまり基になるクラスターで従来 AG の構成で、1 つのレプリカは、WSFC と別のペースの Linux コンピューターにすることはできません。

クラスター型なしの可用性グループには、OS 境界を越えることがあるため Linux と Windows ベースの両方のレプリカ、同じ可用性グループ レプリカはそのことができます。 例を示します、プライマリ レプリカが Windows ベース セカンダリ上にある Linux ディストリビューションのいずれか。

![ハイブリッドなし](./media/sql-server-linux-availability-group-overview/image1.png)

分散型可用性グループでは、OS の境界を越えることができますも。 構成方法、外部の中で構成されているいずれかなどの基になる Ag は、ルールによってバインドされる Linux のみが、WSFC を使用して、可用性グループに参加していることを構成する可能性があります。 次の例を参照してください。

![ハイブリッド Dist AG](./media/sql-server-linux-availability-group-overview/image2.png)

<!-- Distributed AGs are also supported for upgrades from [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] to [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. For more information on how to achieve this, see [the article “x”].

If using automatic seeding with a distributed availability group that crosses OSes, it can handle the differences in folder structure. How this works is described in [the documentation for automatic seeding].
-->
 
## <a name="next-steps"></a>次の手順
[Linux 上の SQL Server の可用性グループを構成します。](sql-server-linux-availability-group-configure-ha.md)

[SQL Server on Linux の読み取りのスケールの可用性グループを構成します。](sql-server-linux-availability-group-configure-rs.md)

[RHEL で可用性グループのクラスター リソースを追加します。](sql-server-linux-availability-group-cluster-rhel.md)

[SLES で可用性グループのクラスター リソースを追加します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu で可用性グループのクラスター リソースを追加します。](sql-server-linux-availability-group-cluster-ubuntu.md)

[クロス プラットフォームの可用性グループを構成します。](sql-server-linux-availability-group-cross-platform.md)

