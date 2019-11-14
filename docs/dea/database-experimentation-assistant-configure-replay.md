---
title: SQL Server アップグレードの再生の構成
description: Database Experimentation Assistant での再生の構成
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: b58233e40e27908f0bc8b03a95455216de2c119c
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056718"
---
# <a name="configure-replay-in-database-experimentation-assistant"></a>Database Experimentation Assistant での再生の構成

Database Experimentation Assistant (DEA) は、SQL Server インストールの分散再生ツールを使用して、アップグレードされたテスト環境に対してキャプチャされたトレースを再生します。 クエリが適切に再生されるように、完全な再生を行う前に小さなトレースファイルを使用してテストの実行を行うことをお勧めします。

## <a name="distributed-replay-requirements"></a>分散再生の要件

- 分散再生コントローラーコンピューターで IRF ファイルを作成するには、ハードドライブ領域の78% が追加で必要です。
- 200 MB または 512 MB は、実稼働トレースまたはパフォーマンストレースのキャプチャに使用する理想的なトレースロールオーバーサイズです。   
- 分散再生コントローラーとクライアントコンピューターの CPU と RAM の最小要件は、3.5 GB の RAM を搭載したシングルコア CPU です。
- 1つのコントローラーと4つの子マシンが運用トレースの再生に使用されるため、再生時間はキャプチャ時間より約1.55 倍になります。
- 実稼働およびパフォーマンスのトレース定義ファイルの "公開済み" バージョンを使用し、パフォーマンストレース定義によって対象の1つのデータベースのトレースが除外される場合、分析では、**パフォーマンストレース**のサイズが**実稼働トレース**のサイズより約15倍大きくなっていることが示されます。

## <a name="set-up-a-virtual-network-or-domain"></a>仮想ネットワークまたはドメインを設定する

分散再生では、コンピューター間で共通のアカウントを使用する必要があります。 この要件のため、セキュリティ上の理由から、仮想ネットワークまたはドメインによって制御されるネットワーク上で分散再生を実行することをお勧めします。

- 環境にコントローラーとクライアントコンピューターを作成します。
- コントローラーとクライアントコンピューターがネットワーク経由で相互に ping できることを確認します。
- 分散再生クライアントコンピューターは、SQL Server を実行している再生ターゲットコンピューターに接続されている必要があります。

## <a name="set-up-the-controller-service"></a>コントローラーサービスの設定

コントローラーサービスを設定するには:

1. SQL Server インストーラーを使用して、分散再生コントローラーをインストールします。 分散再生コントローラーを構成する SQL Server インストーラーウィザードの手順をスキップした場合は、構成ファイルを使用してコントローラーを構成できます。 一般的なインストールでは、構成ファイルは C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayController\DReplayController.config. にあります。
1. 分散再生コントローラーのログは、C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayController\Log. にあります。
1. Services.msc を開き、 **SQL Server 分散再生 Controller**サービスにアクセスします。
1. サービスを右クリックし、 **[プロパティ]** を選択します。 サービスアカウントを、ネットワーク内のコントローラーとクライアントコンピューターに共通のアカウントに設定します。
1. **[OK]** を選択して、 **[プロパティ]** ウィンドウを閉じます。
1. Services.msc から**SQL Server 分散再生 Controller**サービスを再起動します。 また、コマンドラインで次のコマンドを実行して、サービスを再起動することもできます。<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
1. 構成オプションの詳細については、「 [Configure 分散再生](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay)」を参照してください。

## <a name="configure-dcom"></a>DCOM を構成する

この構成は、コントローラーコンピューターでのみ必要です。

1. Dcomcnfg.exe を開きます。
1. [**コンポーネントサービス** > **コンピュータ** > **マイコンピューター** > **DCOM 構成**] を展開します。
1. **DCOM の構成**、右クリック**dreplaycontroller**、し、**プロパティ**します。
1. **[セキュリティ]** タブをクリックします。
1. **[起動とアクティブ化のアクセス許可]** で、 **[カスタマイズ]** を選択し、 **[編集]** を選択します。
1. 再生を開始するユーザーを追加します。 ユーザーにローカル起動とローカルのアクティブ化のアクセス許可を与えます。 ユーザーがリモートでの起動またはアクティブ化を計画している場合は、[リモート起動] と [リモートからのアクティブ化] のアクセス許可をユーザーに付与します。
1. **[OK]** を選択して変更をコミットし、 **[セキュリティ]** タブに戻ります。
1. **[アクセス許可]** で **[カスタマイズ]** を選択し、 **[編集]** を選択します。
1. 再生を開始するユーザーを追加します。 ユーザーにローカルアクセス許可を与えます。 ユーザーがコントローラーサービスへのリモートアクセスを計画している場合は、ユーザーにリモートアクセス権限を付与します。
1. **[OK]** を選択して変更をコミットし、 **[セキュリティ]** タブに戻ります。
1. **[OK]** を選択して変更をコミットします。
1. Services.msc から SQL Server 分散再生 Controller サービスを再起動します。 また、コマンドラインで次のコマンドを実行して、サービスを再起動することもできます。<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>クライアントサービスを設定する

クライアントサービスをセットアップする前に、ping などのネットワークツールを使用して、コントローラーとクライアントコンピューターが通信できることを確認します。

1. SQL Server インストーラーを使用して分散再生クライアントをインストールします。
1. Services.msc を開き、SQL Server 分散再生クライアントサービスにアクセスします。
1. サービスを右クリックし、 **[プロパティ]** を選択します。 サービスアカウントを、ネットワーク内のコントローラーコンピューターとクライアントコンピューターの両方に共通するアカウントに設定します。
1. **[OK]** を選択して、 **[プロパティ]** ウィンドウを閉じます。 分散再生クライアントを構成するために SQL Server インストーラーウィザードの手順をスキップした場合は、構成ファイルを使用して構成できます。 一般的なインストールでは、構成ファイルは C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayClient\DReplayClient.config. にあります。
1. DReplayClient .config ファイルにコントローラーとして登録するためのコントローラーの名前が含まれていることを確認します。
1.  Services.msc から SQL Server 分散再生クライアントサービスを再起動します。 また、コマンドラインから次のコマンドを実行してサービスを再起動することもできます。<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
1. 分散再生コントローラーのログは、C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayClient\Log. にあります。 ログには、クライアントが自身をコントローラーに登録できるかどうかが示されます。
1. 構成が成功した場合、ログには "コントローラー < コントローラー名\>に登録されています" というメッセージが表示されます。
1. 構成オプションの詳細については、「 [Configure 分散再生](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay)」を参照してください。

## <a name="set-up-distributed-replay-administration-tools"></a>分散再生管理ツールのセットアップ

分散再生管理ツールを使用すると、分散再生が環境内で適切に機能しているかどうかをすばやくテストできます。 構成のテストは、複数のクライアントコンピューターがコントローラーに登録されている環境で特に役立ちます。 管理ツールを入手するには、SQL Server Management Studio (SSMS) のインストールが必要になる場合があります。

1. SSMS のインストール場所に移動し、分散再生管理ツールの dreplay とその依存コンポーネントを探します。
1. コマンドプロンプトウィンドウを開き、`dreplay.exe status -f 1`を実行します。
1. 上記のすべての手順が成功した場合、コンソール出力は、コントローラーがクライアントを `READY` 状態で認識できることを示しています。

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>リモート分散再生アクセスできるようにファイアウォールを構成する

分散再生にリモートでアクセスするには、ドメインまたは仮想ネットワーク内に表示されているポートを開く必要があります。

1. **[セキュリティが強化**された**Windows ファイアウォール**] を開きます。
1. **[受信の規則]** にアクセスします。
1. プログラム C:\Program Files (x86) \Microsoft SQL Server\<バージョン\>\Tools\DReplayController\DReplayController.exe. の新しい受信ファイアウォール規則を作成します。
1. DReplayController のすべてのポートに対するドメインレベルのアクセスを許可して、コントローラーサービスとリモートで通信できるようにします。
1. ルールを保存します。

## <a name="set-up-target-computers"></a>ターゲットコンピューターの設定

A/B テストまたは実験を実行するには、2つの再生が必要です。 つまり、移行シナリオには、SQL Server インストールの2つのインスタンスが必要になることがあります。 

同じコンピューターに2つのバージョンの SQL Server インスタンスをインストールすることもできます。 注意事項は、再生の進行中にインスタンスが完全に分離されていることを確認することです。

再生ごとに次の手順を実行する必要があります。

1. データベースのバックアップを復元します。
1. SQL Server インスタンスのデータベースにアクセスするためのアクセス許可をクライアントサービスアカウントユーザーに付与します。 SQL Server インスタンスでクエリを実行するには、権限が必要です。
1. 再生を開始します。

## <a name="next-steps"></a>次の手順

- アップグレードされたテスト環境でキャプチャされたトレースを再生する方法については、「[再生トレース](database-experimentation-assistant-replay-trace.md)」を参照してください。

- DEA とデモの19分の概要については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
