---
title: SQL 操作 Studio (プレビュー) の機能を拡張 |Microsoft ドキュメント
description: SQL 操作 Studio (プレビュー) に拡張機能を追加します。
ms.custom: tools|sos
ms.date: 03/28/2018
ms.reviewer: alayu; erickang; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40b29dfb7512c0f38f009b635ab610cebce7a07a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="extend-the-functionality-of-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] の機能を拡張します

[!INCLUDE[name-sos](../includes/name-sos-short.md)] の拡張機能はベース [!INCLUDE[name-sos](../includes/name-sos-short.md)] のインストールにより多くの機能を簡単に追加する方法を提供します。

拡張機能は、SQL Operations Studio チーム (Microsoft) だけでなく、サード パーティ コミュニティ (あなた!) によって提供されます。拡張機能を作成する方法については [拡張機能の概要](https://github.com/Microsoft/sqlopsstudio/wiki/Getting-started-with-Extensibility) を参照してください。


## <a name="add-sql-operations-studio-extensions"></a>SQL Operations Studio の拡張機能の追加

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. 使用可能な拡張機能を選択して詳細を表示します。

   ![拡張機能マネージャー](media/extensions/extension-manager.png)

3. 必要な拡張機能を選択し、**インストール**します。
4. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。
5. サーバーまたはデータベースを右クリックし、**管理**を選択して管理ダッシュ ボードに移動します。
6. インストールされた拡張機能は、管理ダッシュ ボードのタブとして表示されます。

   ![拡張機能マネージャー](media/extensions/dashboard-extensions.png)
