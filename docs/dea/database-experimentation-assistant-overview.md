---
title: アップグレードする SQL Server の Database 実験 Assistant ソリューションの概要
description: データベースの実験のアシスタントの概要
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: 1183c6a443406f6031453b876f9165257db82c07
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058898"
---
# <a name="overview-of-database-experimentation-assistant"></a>データベースの実験のアシスタントの概要

データベース実験アシスタント (DEA) は、SQL Server のアップグレード実験ソリューションです。 DEA 対象のバージョンが SQL Server の特定のワークロードを評価することができます。 以前の SQL Server バージョン (2005年以降) から SQL Server の最新のバージョンにアップグレードしたお客様は、ツールで提供される分析のメトリックを使用できます。 

DEA 分析のメトリックは次のとおりです。
- 互換性エラーが発生したクエリ
- 低下したクエリおよびクエリ プラン
- その他のワークロード比較データ

データの比較については、信頼性の高いと、正常なアップグレード エクスペリエンスにつながります。

DEA とデモを 19 分については、次のビデオをご覧ください。

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

## <a name="get-dea"></a>DEA を取得します。

DEA をインストールする[ダウンロード](https://www.microsoft.com/download/details.aspx?id=54090)ツールの最新バージョン。 実行し、 **DatabaseExperimentationAssistant.exe**ファイル。

## <a name="solution-architecture-for-comparing-workloads"></a>ワークロードを比較するためのソリューション アーキテクチャ

次の図は、ワークロードの比較については、ソリューションのアーキテクチャを示します。 ワークロードの比較は、SQL Server 2008 から SQL Server 2016 へのアップグレード中に DEA および Distributed Replay を使用します。

![ワークロード比較ソリューションのアーキテクチャ](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>DEA の前提条件

以下は、DEA を実行するためのいくつかの前提条件です。
- ハードウェアの最小要件:3.5 GB の RAM、シングルコア マシン。
- 最適なハードウェア要件:(3.5 GB RAM 以上の) と 8 コア CPU。 プロセッサを 8 個を超えるコアを搭載 DEA ランタイムを強化します。
- さらに 33% のパフォーマンス トレースのサイズは、店 A、B、およびレポートの分析データベースに必要です。

## <a name="configure-dea"></a>DEA を構成します。

前提条件となる環境のアーキテクチャ推奨 DEA をインストールする*分散再生コント ローラーと同じコンピューター上*します。 この実習では、コンピューター間の呼び出しを回避し、構成を簡略化します。

### <a name="required-configuration-for-workload-comparison-by-using-dea"></a>DEA を使用してワークロードの比較のために必要な構成

DEA は、Windows 認証を使用して、データベース サーバーに接続します。 DEA を実行しているユーザーは、Windows 認証を使用してデータベース サーバー (ソース、ターゲット、および分析) に接続できることを確認します。

**構成要件をキャプチャ**:

*   DEA を実行しているユーザーは、Windows 認証を使用して、ソース データベース サーバーに接続できます。
*   DEA を実行しているユーザーは、ソース データベース サーバー上の sysadmin 権限を持っています。
*   ソース データベース サーバーを実行してサービス アカウントでは、トレース フォルダーのパスへの書き込みアクセスを持っています。

詳細については、次を参照してください、[キャプチャに関する FAQ。](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture)

**構成要件を再生**: 

*   DEA を実行しているユーザーは、Windows 認証を使用して、ターゲット データベース サーバーに接続できます。
*   DEA を実行しているユーザーは、ターゲット データベースのサーバーで sysadmin 権限を持っています。
*   対象のデータベース サーバーを実行しているサービス アカウントでは、トレース フォルダーのパスへの書き込みアクセスを持っています。
*   分散再生クライアントを実行しているサービス アカウントは、Windows 認証を使用して、ターゲット データベース サーバーに接続できます。
*   DEA は COM インターフェイスを使用して Distributed Replay controller と通信します。 分散再生コント ローラー上の受信要求の TCP ポートが開いていることを確認します。

詳細については、次を参照してください、[再生に関する FAQ。](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay)

**分析の構成要件**: 

*   DEA を実行しているユーザーは、Windows 認証を使用して、分析データベース サーバーに接続できます。
*   DEA を実行しているユーザーは、ソース データベース サーバー上の sysadmin 権限を持っています。

詳細については、次を参照してください、[分析に関する FAQ。](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports)

## <a name="set-up-telemetry"></a>製品利用統計情報を設定します。

DEA が Microsoft に製品利用統計情報を送信するインターネット対応機能です。 Microsoft は、製品のエクスペリエンスを強化するためにテレメトリを収集します。 製品利用統計情報は省略可能です。 収集される情報は、local audit のコンピューターにも保存されます。 常に、収集される情報を確認できます。 DEA からのすべてのログ ファイルは、%temp% に保存されます\\DEA フォルダー。

収集するイベントを決定できます。 また、収集されたイベントを Microsoft に送信されるかどうかも決定します。 イベントの 4 つの種類があります。

*   **TraceEvent**:アプリケーション (たとえば、「トリガーされた停止キャプチャ」) の使用状況イベント。
*   **例外**:アプリケーションの使用状況の中にスローされる例外。
*   **DiagnosticEvent**:問題が発生したときに、診断を支援するために、イベント ログ (*いない*Microsoft に送信される)。
*   **FeedbackEvent**:アプリケーションを使用して送信されるユーザーからのフィードバック。

次の手順は、収集するイベントを選択する方法を説明し、Microsoft にイベントを送信するかどうか。

1.  DEA がインストールされている場所に移動 (たとえば、c:\\Program Files (x86)\\Microsoft Corporation\\データベース実験アシスタント)。
2.  2 つの .config ファイルを開きます。(アプリケーション) の DEA.exe.config と DEACmd.exe.config (CLI) のです。
3.  イベントの種類の収集を停止するには、値を設定*イベント*(たとえば、 **TraceEvent**) に**false**します。 もう一度イベントの収集を開始するに値を設定します。 **true**します。
4.  イベントのローカル コピーの保存を停止するには、値を設定**TraceLoggerEnabled**に**false**します。 ローカル コピーをもう一度保存を開始する値を設定**true**します。
5.  イベントを Microsoft に送信を停止するには、値を設定**AppInsightsLoggerEnabled**に**false**します。 もう一度 Microsoft にイベントの送信を開始する値を設定**true**します。

DEA に準拠するもの、 [Microsoft プライバシーに関する声明](https://aka.ms/dea-privacy)します。

## <a name="next-steps"></a>次の手順

[開始](database-experimentation-assistant-get-started.md)キャプチャ、再生、およびトレースを分析に必要な手順について説明します。
