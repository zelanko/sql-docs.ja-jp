---
title: 有効にするにまたは使用状況データ収集を無効にしてクラッシュ レポートの SQL 操作 Studio (プレビュー) |Microsoft ドキュメント
description: この記事では、使用状況とクラッシュ レポート データは収集されマイクロソフトに送信される場合を制御する方法について説明します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 035195a03dea60f097a9de88ceb869fe53398c35
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>有効にするにまたはの使用状況データ収集を無効にします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>製品利用統計情報の報告を無効にする方法

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 使用状況データを収集し、製品とサービスの向上に協力を Microsoft に送信します。 詳細については、読み取り、[のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409)です。

使用状況データを Microsoft に送信しない場合は、設定、 *telemetry.enableTelemetry*設定*false*です。

すべてのテレメトリ イベントをミュートする[!INCLUDE[name-sos](../includes/name-sos-short.md)]から**ファイル** > **設定** > **設定**、次のオプションを追加。

```json
    "telemetry.enableTelemetry": false
```

**重要な注意**: このオプションの再起動が必要に[!INCLUDE[name-sos](../includes/name-sos-short.md)]を有効にします。 

## <a name="how-to-disable-crash-reporting"></a>クラッシュ レポートを無効にする方法

クラッシュ レポートを無効にするから**ファイル** > **環境設定** > **設定**、次のオプションを追加します。

```json
    "telemetry.enableCrashReporter": false
```

**重要な注意**: このオプションの再起動が必要に[!INCLUDE[name-sos](../includes/name-sos-short.md)]を有効にします。

## <a name="additional-resources"></a>その他のリソース
- [ワークスペースとユーザーの設定](settings.md)