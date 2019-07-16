---
title: 有効にするか、使用状況データ収集、およびクラッシュの報告を無効にします。
titleSuffix: Azure Data Studio
description: この記事では、使用状況とクラッシュ レポート データを収集し、Microsoft に送信される場合を制御する方法について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 71ed86e9ad076a41099eaf4e56fe67a25b5f2c21
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958944"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>有効にするかの使用状況データ収集を無効にします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>テレメトリの報告を無効にする方法

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 使用状況データ収集され、マイクロソフトの製品およびサービスを向上させるために Microsoft に送信されます。 詳細については、参照、[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409)します。

使用状況データを Microsoft に送信しない場合は設定できます、 *telemetry.enableTelemetry*設定*false*します。

すべてのテレメトリ イベントをミュートする[!INCLUDE[name-sos](../includes/name-sos-short.md)]から**ファイル** > **設定** > **設定**、次のオプションの追加。

```json
    "telemetry.enableTelemetry": false
```

**重要なお知らせ**:このオプションは、の再起動を伴う[!INCLUDE[name-sos](../includes/name-sos-short.md)]を有効にします。 

## <a name="how-to-disable-crash-reporting"></a>クラッシュ レポートを無効にする方法

クラッシュ レポートを無効にするから**ファイル** > **設定** > **設定**、次のオプションの追加。

```json
    "telemetry.enableCrashReporter": false
```

**重要なお知らせ**:このオプションは、の再起動を伴う[!INCLUDE[name-sos](../includes/name-sos-short.md)]を有効にします。

## <a name="additional-resources"></a>その他の資料
- [ワークスペースとユーザーの設定](settings.md)
