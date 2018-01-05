---
title: "SQL 操作 Studio (プレビュー) のユーザーとワークスペースの設定 |Microsoft ドキュメント"
description: "SQL 操作 Studio (プレビュー) のユーザーとワークスペースの設定を変更する方法。"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2edea069c05e7ac0316042250f336f1a8c455af0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="user-and-workspace-settings"></a>ユーザーとワークスペースの設定

構成が容易である[!INCLUDE[name-sos](../includes/name-sos-short.md)]好みに応じて設定を使用します。 ほぼすべての部分[!INCLUDE[name-sos](../includes/name-sos-short.md)]のエディター、ユーザー インターフェイス、および機能の動作がオプションを変更できます。

[!INCLUDE[name-sos](../includes/name-sos-short.md)]2 つのさまざまなスコープの設定を提供します。

* **ユーザー**の任意のインスタンスにこれらの設定がグローバルに適用[!INCLUDE[name-sos](../includes/name-sos-short.md)]を開きます。
* **ワークスペース**ワークスペースの設定は、コンピューター上のフォルダーに固有の設定とは、フォルダーをエクスプ ローラー サイドバーで開いている場合にのみ使用できます。 このスコープで定義された設定は、ユーザーのスコープをオーバーライドします。

## <a name="creating-user-and-workspace-settings"></a>ユーザーとワークスペースの設定を作成します。

メニュー コマンド**ファイル** > **設定** > **設定**(**コード** >  **設定** > **設定**Mac 上) はユーザーとワークスペースの設定を構成するエントリ ポイントを提供します。 既定の設定の一覧が表示されます。 適切な変更する設定をコピー`settings.json`ファイル。 右側のタブを使用して、ユーザーとワークスペースの設定ファイル間をすばやく移動できます。

ユーザーとワークスペースの設定を開くことも、**コマンド パレット**(**Ctrl + Shift + P**) と**設定: ユーザー設定を開く**と**開いているワークスペースの設定を設定します。**キーボード ショートカットを使用するか (**Ctrl +**)。

次の例では、エディターで行番号を無効にし、行のテキスト エディターのサイズに基づいて自動的にラップするように構成します。

![設定の例](media/settings/sample-settings.png)

設定の変更がによって再度読み込まれる[!INCLUDE[name-sos](../includes/name-sos-short.md)]変更した後`settings.json`ファイルを保存します。

>**注:**ワークスペースの設定は、チーム全体のプロジェクトに固有の設定を共有するために役立ちます。

## <a name="settings-file-locations"></a>設定ファイルの場所

、プラットフォームによっては、ユーザー設定ファイルはここで。

* **Windows**`%APPDATA%\sqlops\User\settings.json`
* **Mac**`$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux**`$HOME/.config/sqlops/User/settings.json`

ワークスペースの設定ファイルが下にある、`.[!INCLUDE[name-sos](../includes/name-sos-short.md)]`プロジェクトのフォルダーにします。


## <a name="additional-resources"></a>その他のリソース

[!INCLUDE[name-sos](../includes/name-sos-short.md)]から Visual Studio Code、設定の詳細情報の機能は、ユーザーとワークスペースの設定を継承、 [Visual Studio Code の設定を](https://code.visualstudio.com/docs/getstarted/settings)資料です。