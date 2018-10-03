---
title: Azure Data Studio での統合ターミナル |Microsoft Docs
description: Azure Data Studio の統合ターミナルについて説明します。
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: fd4b55c8ee4389b6318585842047dbaf6ac1c220
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039188"
---
# <a name="integrated-terminal"></a>統合ターミナル

[!INCLUDE[name-sos](../includes/name-sos-short.md)]、最初に、ワークスペースのルートから始まり、統合ターミナルを開くことができます。 これは、windows を切り替えるか、クイック コマンド ライン タスクを実行する既存の端末の状態を変更する必要はありません、便利です。

ターミナルを開きます。

* 使用して、 **Ctrl +'** アクサン グラーブ文字をキーボード ショートカット。
* 使用して、**ビュー** | **統合ターミナル**メニュー コマンド。
* **コマンド パレット**(**Ctrl + Shift + P**) を使用して、**表示の切り替えの統合ターミナル**コマンド。

![ターミナル](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> エクスプ ローラーで外部シェルを開くことができますも**コマンド プロンプトで開く**コマンド (**ターミナルで開く**Mac または Linux で) 外の共同作業する場合[!INCLUDE[name-sos](../includes/name-sos-short.md)]します。

## <a name="managing-multiple-terminals"></a>複数の端末を管理します。

複数の端末に別の場所を作成し、それらの間を簡単に移動できます。 押して、プラス アイコンの右上でターミナルのインスタンスを追加することができます、**ターミナル** パネルまたはトリガーによって、 **Ctrl + Shift +'** コマンド。 これにより、それらを切り替えるために使用できるドロップダウン リストで別のエントリが作成されます。

![複数の端末](media/integrated-terminal/terminal-multiple-instances.png)

ごみ箱を押してターミナル インスタンスを削除できるボタンをクリックします。

> [!TIP]
> 複数端末を広範に使用する場合のキー バインドを追加することができます、 `focusNext`、`focusPrevious`と`kill`に記載されているコマンド、[キー バインディング セクション](#key-bindings)キーボードのみを使用してそれらの間を移動できるようにします。

## <a name="configuration"></a>構成

シェルに使用される既定値は`$SHELL`Linux、macOS、Windows 10 で PowerShell と Windows の以前のバージョンで cmd.exe でします。 設定を手動でオーバーライドできます`terminal.integrated.shell.*`で[設定](settings.md)します。 引数は、Linux と macOS を使用してターミナル シェルに渡すことができます、`terminal.integrated.shellArgs.*`設定します。

### <a name="windows"></a>Windows

Windows で、シェルを正しく構成するには適切な実行可能ファイルを特定し、設定を更新します。 一般的なシェルの実行可能ファイルと既定の場所の一覧を次に示します。

```json
// 64-bit cmd if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\cmd.exe"
// 64-bit PowerShell if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\WindowsPowerShell\\v1.0\\powershell.exe"
// Git Bash
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
// Bash on Ubuntu (on Windows)
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\bash.exe"
```

> [!NOTE]
> 統合ターミナルとして使用される、シェルの実行可能ファイルがコンソール アプリケーションをある必要がありますように`stdin/stdout/stderr`リダイレクトできます。

> [!TIP]
> 統合ターミナル シェルがの権限で実行されている[!INCLUDE[name-sos](../includes/name-sos-short.md)]します。 管理者特権 (管理者) または別の権限を持つシェル コマンドを実行する必要がある場合、プラットフォームのユーティリティをなど、使用できる`runas.exe`ターミナル内。

### <a name="shell-arguments"></a>シェルの引数

起動時に引数をシェルに渡すことができます。

たとえば、ログイン シェルとして bash を実行中に有効にするため (実行に使用する`.bash_profile`)、渡す、 `-l` (二重引用符) を使用して引数。

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>端末のディスプレイの設定

次の設定では、統合ターミナルのフォントと行の高さをカスタマイズできます。

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>ターミナルのキー バインド

**ビュー: トグル統合ターミナル**にコマンドがバインドされている**Ctrl +'** ビューとの間の統合ターミナル パネルをすばやく切り替える。

統合ターミナル内のナビゲーションを迅速にキーボード ショートカットを次に示します。

Key|コマンド
---|---
**Ctrl +'**|統合ターミナルを表示します。
**Ctrl + Shift +'**|新しいターミナルを作成します。
**Ctrl + ↑**|上にスクロール
**Ctrl キーを押しながら下方向**|下にスクロール
**Ctrl キーを押しながら PageUp**|ページにスクロール
**Ctrl + PageDown**|ページを下にスクロール
**Ctrl + ホーム**|一番上にスクロールします。
**Ctrl + end**|一番下までスクロールします。
**Ctrl + K**|ターミナルをクリアします。

その他のターミナル コマンドは、使用、好みのキーボード ショートカット キーにバインドすることができます。

これらは次のとおりです。

* `workbench.action.terminal.focus`: 端末の焦点を当てます。 これは、切り替えのようなものですが、表示されている場合、非表示ではなくターミナル重点を置いています。
* `workbench.action.terminal.focusNext`: 次の端末のインスタンスについて説明します。
* `workbench.action.terminal.focusPrevious`: 以前のターミナル インスタンスをについて説明します。
* `workbench.action.terminal.kill`: 現在のターミナルのインスタンスを削除します。
* `workbench.action.terminal.runSelectedText`: ターミナルのインスタンスで、選択したテキストを実行します。
* `workbench.action.terminal.runActiveFile`: ターミナルのインスタンスでアクティブなファイルを実行します。

### <a name="run-selected-text"></a>選択したテキストの実行

使用する、`runSelectedText`コマンド、エディターでテキストを選択し、コマンドを実行**ターミナル: アクティブなターミナルで選択したテキストの実行**を使用して、**コマンド パレット**(**Ctrl + Shift + P**). 端末は、選択したテキストを実行しようとします。

![選択したテキストを実行します。](media/integrated-terminal/terminal_run_selected.png)

アクティブなエディターでテキストが選択されていない場合は、上にカーソルが行が、ターミナルで実行されます。

### <a name="copy--paste"></a>コピーと貼り付け

コピーと貼り付けのキー バインドでは、プラットフォームの標準に従います。

* Linux: **Ctrl + Shift + C**と**Ctrl + Shift + V**
* Mac の場合: **Cmd キーを押しながら C キー**と**Cmd キーを押しながら V キー**
* Windows: **Ctrl + C**と**Ctrl + V**

### <a name="find"></a>[検索]

統合ターミナルでトリガーできる基本的な検索機能を持つ**Ctrl + F**します。

場合**Ctrl + F** Linux、Windows で、検索ウィジェットを起動するのではなくシェルに移動するには、キー バインドを削除する必要がありますようになります。

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>ターミナル セッションの名前を変更します。

使用して統合ターミナル セッションを変更することができますようになりました、**ターミナル: 名前を変更**(`workbench.action.terminal.rename`) コマンド。 新しい名前は、ターミナルの選択ドロップダウンに表示されます。

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>ターミナルを通過する強制のキー バインド

統合ターミナルでフォーカスがあるときに、キーストロークに渡されは端末自体によって消費されるため、多くのキー バインドは機能しません。 `terminal.integrated.commandsToSkipShell`設定は、この問題を回避するために使用できます。 キー バインドは、シェルによって処理をスキップし、代わりに、によって処理されるコマンド名の配列が含まれている、[!INCLUDE[name-sos](../includes/name-sos-short.md)]バインド システムのキーします。 既定では、選択のいくつか一般的に使用されるキー バインドだけでなく、すべてのターミナル キー バインドが含まれます。

