---
title: SQL 操作 Studio (プレビュー) のユーザーとワークスペースの設定 |Microsoft ドキュメント
description: SQL 操作 Studio (プレビュー) のユーザーとワークスペースの設定を変更する方法。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbabb96b46a7054ed22daf034413df05c903e553
ms.sourcegitcommit: 31df356f89c4cd91ba90dac609a7eb50b13836de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="user-and-workspace-settings"></a>ユーザーとワークスペースの設定

構成が容易である[!INCLUDE[name-sos](../includes/name-sos-short.md)]好みに応じて設定を使用します。 ほぼすべての部分[!INCLUDE[name-sos](../includes/name-sos-short.md)]のエディター、ユーザー インターフェイス、および機能の動作がオプションを変更できます。

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 2 つのさまざまなスコープの設定を提供します。

* **ユーザー**の任意のインスタンスにこれらの設定がグローバルに適用[!INCLUDE[name-sos](../includes/name-sos-short.md)]を開きます。
* **ワークスペース**ワークスペースの設定は、コンピューター上のフォルダーに固有の設定とは、フォルダーをエクスプ ローラー サイドバーで開いている場合にのみ使用できます。 このスコープで定義された設定は、ユーザーのスコープをオーバーライドします。

## <a name="creating-user-and-workspace-settings"></a>ユーザーとワークスペースの設定を作成します。

メニュー コマンド**ファイル** > **設定** > **設定**(**コード** >  **設定** > **設定**Mac 上) はユーザーとワークスペースの設定を構成するエントリ ポイントを提供します。 既定の設定の一覧が表示されます。 適切な変更する設定をコピー`settings.json`ファイル。 右側のタブを使用して、ユーザーとワークスペースの設定ファイル間をすばやく移動できます。

ユーザーとワークスペースの設定を開くことも、**コマンド パレット**(**Ctrl + Shift + P**) と**設定: ユーザー設定を開く**と**開いているワークスペースの設定を設定します。**キーボード ショートカットを使用するか (**Ctrl +**)。

次の例では、エディターで行番号を無効にし、コード行を自動的にインデントを設定するように構成します。

![設定の例](media/settings/sample-settings.png)

設定の変更がによって再度読み込まれる[!INCLUDE[name-sos](../includes/name-sos-short.md)]変更した後`settings.json`ファイルを保存します。

>**注:** ワークスペースの設定は、チーム全体のプロジェクトに固有の設定を共有するために役立ちます。

## <a name="settings-file-locations"></a>設定ファイルの場所

、プラットフォームによっては、ユーザー設定ファイルはここで。

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

ワークスペースの設定ファイルが下にある、`.[!INCLUDE[name-sos](../includes/name-sos-short.md)]`プロジェクトのフォルダーにします。

## <a name="hot-exit"></a>ホット終了

SQL 操作の Studio を忘れずに未保存の変更ファイル既定で終了するとします。 これは、Visual Studio のコードでホット終了機能と同じです。

既定では、ホット終了は off です。 ホットを有効にする終了を編集して、`files.hotExit`設定します。 詳細については、「 [(Visual Studio コードのドキュメント) にホットの終了](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit)です。


## <a name="tab-color"></a>タブの色

簡単に使用しているどのような接続を識別するをエディターで開いているタブは、接続が所属するサーバー グループの色を一致するように設定するそれぞれの色を持つことができます。 既定では、タブの色は既定で無効です。 編集することによって、タブの色を有効にする、`sql.tabColorMode`設定します。

## <a name="additional-resources"></a>その他のリソース

[!INCLUDE[name-sos](../includes/name-sos-short.md)]から Visual Studio Code、設定の詳細情報の機能は、ユーザーとワークスペースの設定を継承、 [Visual Studio Code の設定を](https://code.visualstudio.com/docs/getstarted/settings)資料です。
