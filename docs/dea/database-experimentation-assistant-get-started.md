---
title: ワークロード比較プロセスの概要
description: Database Experimentation Assistant (DEA) は、アップグレードや新しいインデックスなど、SQL Server 環境で変更を行うための A/B テストソリューションです。
ms.date: 11/16/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 18cba7abf0d73197c248a62283d52126873169a3
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165750"
---
# <a name="overview-of-the-workload-comparison-process"></a>ワークロード比較プロセスの概要

Database Experimentation Assistant (DEA) を使用すると、(現在の環境の) 移行元サーバーのワークロードが新しい環境でどのように動作するかを評価できます。 DEA では、次の3つの段階を実行して A/B テストを実行します。

- 移行元サーバーでワークロードトレースをキャプチャする。
- ターゲット1とターゲット2でキャプチャされたワークロードトレースを再生しています。
- ターゲット1とターゲット2から収集された、再生されたワークロードトレースを分析しています。

この記事では、このプロセスの概要について説明します。

## <a name="capturing-a-workload-trace"></a>ワークロードトレースのキャプチャ

A/B テスト SQL Server の最初の段階では、移行元サーバーでトレースをキャプチャします。 通常、移行元サーバーは運用サーバーです。 トレースファイルは、タイムスタンプを含む、そのサーバー上のクエリワークロード全体をキャプチャします。

注意点 :

- ワークロードトレースのキャプチャを開始する前に、トレースをキャプチャしているデータベースを必ずバックアップしてください。
- DEA ユーザーは、Windows 認証を使用してデータベースに接続するように構成する必要があります。
- SQL Server サービスアカウントには、ソーストレースファイルのパスへのアクセス権が必要です。
- DEA でクエリのパフォーマンスが向上したか低下しているかを判断するには、そのクエリがキャプチャ期間中に少なくとも15回実行される必要があります。

## <a name="replaying-a-workload-trace"></a>ワークロードトレースの再生

A/B テスト SQL Server の2番目の段階では、2つの対象サーバーでキャプチャしたトレースファイルを再生します。

ターゲット1は、提案されたターゲット環境を模倣する移行元サーバーターゲット2を模倣します。

ターゲット1とターゲット2のハードウェア構成は可能な限り同じにする必要があるため、SQL Server では、提案された変更のパフォーマンスへの影響を正確に分析できます。

注意点 :

- ワークロードトレースを再生するには、分散再生 (DReplay) トレースを実行するようにコンピューターを設定する必要があります。
- 移行元サーバーのバックアップを使用して、対象サーバー上のデータベースを復元してください。
- 評価結果の一貫性を向上させるには、サービスアプリケーションで SQL Server サービス (MSSQLSERVER) を再起動することをお勧めします。 SQL Server のクエリキャッシュは、評価結果に影響を与える可能性があります。

## <a name="analyzing-the-replayed-workload-traces"></a>再生されたワークロードトレースの分析

プロセスの最後の段階は、再生トレースを使用して分析レポートを生成することです。 次に、提案された変更によって生じる可能性のあるパフォーマンスへの影響について分析レポートを確認します。

注意点 :

- 1つ以上のコンポーネントが不足している場合は、新しい分析レポートを生成しようとすると (インターネット接続が必要)、[前提条件] ページがダウンロードのリンクと共に表示されます。
- 以前のバージョンのツールで生成されたレポートを表示するには、最初にスキーマを更新する必要があります。

## <a name="see-also"></a>参照

- サーバーで発生するイベントのログを使用してトレースファイルを生成する方法については、「 [Capture trace](database-experimentation-assistant-capture-trace.md)」を参照してください。
