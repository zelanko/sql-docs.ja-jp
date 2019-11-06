---
title: SQL Server のアップグレード データベース実験アシスタントの再生を構成します。
description: データベース実験アシスタントの再生を構成します。
ms.custom: ''
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
ms.openlocfilehash: 9166265dad077d4a3e83cc300868607d001ef233
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058957"
---
# <a name="configure-replay-in-database-experimentation-assistant"></a>データベース実験アシスタントの再生を構成します。

データベース実験アシスタント (DEA) では、SQL Server のインストール、Distributed Replay ツールを使用して、アップグレードされたテスト環境に対してキャプチャしたトレースを再生します。 クエリの適切な再生を完全な再生を実行する前に、トレースの小さなファイルを使用して実行するテストを実行することをお勧めします。

## <a name="distributed-replay-requirements"></a>分散再生の要件

- 分散再生コント ローラー コンピューター IRF ファイルを作成するには、ハード ドライブの空き領域の追加の 78% が必要です。
- 200 MB または 512 MB を使用して実稼働またはパフォーマンス トレースをキャプチャする理想的なトレース ロール オーバーのサイズです。   
- 分散再生コント ローラーとクライアント コンピューターの CPU と RAM の最小要件は、3.5 gb の RAM、シングルコア CPU です。
- 再生時間がかかります約 1.55 回キャプチャ時間よりも 1 つのコント ローラーと 4 つの子のコンピューターが実稼働トレースの再生に使用されるため。
- 分析ことを示しています、「公開」のバージョンの運用、パフォーマンス トレース定義ファイル、トレースをパフォーマンス トレース定義のフィルターを使用して目的の 1 つのデータベースの場合、**パフォーマンス トレース**サイズ約 15 倍、**実稼働トレース**サイズ。

## <a name="set-up-a-virtual-network-or-domain"></a>仮想ネットワークまたはドメインをセットアップします。

Distributed Replay では、マシン間で共通のアカウントを使用する必要があります。 この要件により、およびセキュリティ上の理由は、仮想ネットワーク上またはドメイン管理されたネットワークで分散再生を実行しているお勧めします。

- 環境で、コント ローラーとクライアント マシンを作成します。
- コント ローラーとクライアント コンピューターはネットワーク経由で互いに ping することを確認します。
- 分散再生クライアント コンピューターは、SQL Server を実行している replay ターゲット コンピューターへの接続に必要です。

## <a name="set-up-the-controller-service"></a>コント ローラー サービスをセットアップします。

コント ローラー サービスを設定します。

1. SQL Server インストーラーを使用して分散再生コント ローラーをインストールします。 分散再生コント ローラーを構成する SQL Server インストーラー ウィザードの手順をスキップする場合は、構成ファイルで、コント ローラーを構成できます。 通常のインストール、構成ファイルは C:\Program Files (x86) \Microsoft SQL Server にあります\<バージョン\>\Tools\DReplayController\DReplayController.config します。
1. 分散再生コント ローラーのログは C:\Program Files (x86) \Microsoft SQL Server\<バージョン\>\Tools\DReplayController\Log します。
1. Services.msc を開き、 **SQL Server Distributed Replay Controller**サービス。
1. サービスを右クリックし、**プロパティ**します。 ネットワーク コント ローラーとクライアント コンピューターに共通であるアカウントをサービス アカウントを設定します。
1. 選択**OK**を閉じる、**プロパティ**ウィンドウ。
1. 再起動、 **SQL Server Distributed Replay Controller** Services.msc からサービス。 また、サービスを再起動するためのコマンドラインで次のコマンドを実行することができますも。<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
1. 詳細構成オプションでは、次を参照してください。 [Distributed Replay の構成](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay)します。

## <a name="configure-dcom"></a>DCOM を構成します。

この構成は、コント ローラー マシンにのみ必要です。

1. Dcomcnfg.exe を開きます。
1. 展開**コンポーネント サービス** > **コンピューター** > **コンピューター** > **DCOM の構成**します。
1. **DCOM の構成**、右クリック**dreplaycontroller**、し、**プロパティ**します。
1. **[セキュリティ]** タブをクリックします。
1. **起動とアクティブ化のアクセス許可**を選択します**カスタマイズ**、し、**編集**します。
1. 再生を開始するユーザーを追加します。 ローカルからの起動とローカル アクティブ化のアクセス許可をユーザーに与えます。 ユーザー プランの起動またはリモートでアクティブにする場合は、ユーザーにリモートからの起動とアクティブ化のアクセス許可を付与します。
1. 選択**OK**に戻って変更をコミットする、**セキュリティ**タブ。
1. **アクセス許可**を選択します**カスタマイズ**、し、**編集**します。
1. 再生を開始するユーザーを追加します。 ユーザーのローカルのアクセス許可を付与します。 ユーザーは、コント ローラー サービスをリモートでアクセスする計画をしている場合は、リモート アクセス許可をユーザーに与えます。
1. 選択**OK**に戻って変更をコミットする、**セキュリティ**タブ。
1. 選択**OK**変更をコミットします。
1. Services.msc から SQL Server Distributed Replay Controller サービスを再起動します。 また、サービスを再起動するためのコマンドラインで次のコマンドを実行することができますも。<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>クライアント サービスをセットアップします。

クライアント サービスをセットアップする前に、ping のようなネットワー キング ツールを使用して、コント ローラーとクライアント コンピューターが通信できることを確認します。

1. SQL Server インストーラーを使用して、分散再生クライアントをインストールします。
1. Services.msc を開き、SQL Server 分散再生クライアント サービスに移動します。
1. サービスを右クリックし、**プロパティ**します。 ネットワーク コント ローラーとクライアントの両方のマシンに共通であるアカウントをサービス アカウントを設定します。
1. 選択**OK**を閉じる、**プロパティ**ウィンドウ。 分散再生クライアントを構成する SQL Server インストーラー ウィザードの手順を省略した場合は、構成ファイルで構成できます。 通常のインストール、構成ファイルは C:\Program Files (x86) \Microsoft SQL Server にあります\<バージョン\>\Tools\DReplayClient\DReplayClient.config します。
1. DReplayClient.config ファイルに、登録のコント ローラーとして、コント ローラー マシンの名前が含まれていることを確認します。
1.  Services.msc から SQL Server 分散再生クライアント サービスを再起動します。 また、サービスを再起動するためのコマンドラインから次のコマンドを実行することができますも。<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
1. 分散再生コント ローラーのログは C:\Program Files (x86) \Microsoft SQL Server\<バージョン\>\Tools\DReplayClient\Log します。 ログに記録するかどうか、クライアントに登録するコント ローラー。
1. ログの構成が成功したメッセージが表示されます"コント ローラーに登録されている < コント ローラー名\>"。
1. 詳細構成オプションでは、次を参照してください。 [Distributed Replay の構成](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay)します。

## <a name="set-up-distributed-replay-administration-tools"></a>Distributed Replay 管理ツールをセットアップします。

Distributed Replay 管理ツールを使用すると、環境内で分散再生が正しく機能しているかどうかを簡単にテストします。 構成のテストは、複数のクライアント コンピューターがコント ローラーと登録されている環境で特に役立ちます。 管理ツールを取得する SQL Server Management Studio (SSMS) をインストールする必要があります。

1. Distributed Replay 管理ツールの dreplay.exe とその依存コンポーネントを探し、SSMS のインストール場所に移動します。
1. コマンド プロンプト ウィンドウを開き、実行`dreplay.exe status -f 1`します。
1. 上記のすべての手順が成功した場合は、コンソール出力はコント ローラーでそのクライアントを表示できることを示します、`READY`状態。

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>Distributed Replay のリモート アクセスのためのファイアウォールを構成します。

Distributed Replay をリモートでアクセスするには、ドメインまたは仮想ネットワーク内に表示されているポートを開く必要があります。

1. 開いている**Windows ファイアウォール**で**セキュリティを高度な**します。
1. 移動して**受信規則**します。
1. プログラム C:\Program Files (x86) \Microsoft SQL Server の新しい受信のファイアウォール ルールを作成\<バージョン\>\Tools\DReplayController\DReplayController.exe します。
1. リモート コント ローラー サービスと通信できる DReplayController.exe のすべてのポートへのドメイン レベルのアクセスを許可します。
1. ルールを保存します。

## <a name="set-up-target-computers"></a>ターゲット コンピューターをセットアップします。

2 つの再生は、A の実行に必要な/B テストや実験します。 つまり、移行シナリオの SQL Server のインストールの 2 つのインスタンスを必要があります。 

同じコンピューター上の SQL Server インスタンスの 2 つのバージョンをインストールすることもできます。 注意して、再生中は、インスタンスが完全に分離されているかどうかを確認することです。

各再生、次の手順を実行する必要があります。

1. データベースのバックアップを復元します。
1. SQL Server インスタンスの下のデータベースにアクセスするには、クライアント サービス アカウント ユーザーのアクセス許可を提供します。 アクセス許可は、クエリには、SQL Server インスタンスで実行する必要があります。
1. 再生を開始します。

## <a name="next-steps"></a>次のステップ

- アップグレードされたテスト環境でキャプチャされたトレースを再生する方法については、次を参照してください。[トレースを再生](database-experimentation-assistant-replay-trace.md)します。

- DEA とデモンストレーションを 19 分については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
