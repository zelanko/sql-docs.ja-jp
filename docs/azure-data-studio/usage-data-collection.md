---
title: 有効にするまたは使用状況データの収集を無効にしてクラッシュ レポートを Azure Data Studio |Microsoft Docs
description: この記事では、使用状況とクラッシュ レポート データを収集し、Microsoft に送信される場合を制御する方法について説明します。
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17bcdff85ff4f40b41492095d265bc4c2b503d76
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038972"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>有効にするかの使用状況データ収集を無効にします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>テレメトリの報告を無効にする方法

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 使用状況データ収集され、マイクロソフトの製品およびサービスを向上させるために Microsoft に送信されます。 詳細については、参照、[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409)します。

使用状況データを Microsoft に送信しない場合は設定できます、 *telemetry.enableTelemetry*設定*false*します。

すべてのテレメトリ イベントをミュートする[!INCLUDE[name-sos](../includes/name-sos-short.md)]から**ファイル** > **設定** > **設定**、次のオプションの追加。

```json
    "telemetry.enableTelemetry": false
```

**重要なお知らせ**: このオプションは、の再起動を伴う[!INCLUDE[name-sos](../includes/name-sos-short.md)]を有効にします。 

## <a name="how-to-disable-crash-reporting"></a>クラッシュ レポートを無効にする方法

クラッシュ レポートを無効にするから**ファイル** > **設定** > **設定**、次のオプションの追加。

```json
    "telemetry.enableCrashReporter": false
```

**重要なお知らせ**: このオプションは、の再起動を伴う[!INCLUDE[name-sos](../includes/name-sos-short.md)]を有効にします。

## <a name="additional-resources"></a>その他のリソース
- [ワークスペースとユーザーの設定](settings.md)
