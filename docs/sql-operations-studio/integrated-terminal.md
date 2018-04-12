---
title: SQL Operations Studio (preview) で統合ターミナル |Microsoft ドキュメント
description: SQL Operations Studio (preview) で統合ターミナルについて説明します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
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
ms.openlocfilehash: b55e86314dd075b61dac5751b29fc541fdf1e2c4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="integrated-terminal"></a>統合ターミナル

[!INCLUDE[name-sos](../includes/name-sos-short.md)]、最初に、ワークスペースのルートから、統合の端末を開くことができます。 これは便利ようにウィンドウを切り替えるまたはクイック コマンド ライン タスクを実行する既存のターミナルの状態を変更する必要はありません。

ターミナルで開きます。

* 使用して、 **Ctrl +'**アクサン グラーブ文字でキーボード ショートカット。
* 使用して、**ビュー** | **統合ターミナル**メニュー コマンド。
* **コマンド パレット**(**Ctrl + Shift + P**)、使用して、**ビュー: トグル統合ターミナル**コマンド。

![ターミナル](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> エクスプ ローラーで、外部のシェルを開くことができますも**でコマンド プロンプトを開く**コマンド (**ターミナルで開く**Mac または Linux で) 外で作業したい場合[!INCLUDE[name-sos](../includes/name-sos-short.md)]です。

## <a name="managing-multiple-terminals"></a>複数の端末を管理します。

複数の端末に開かれている別の場所を作成し、それらの間を簡単に移動できます。 右上で、プラス アイコンをクリックしてターミナル インスタンスを追加することができます、**ターミナル**パネルまたはでトリガーする、 **Ctrl + Shift +'**コマンド。 これには、両者を切り替えるに使用できるドロップダウン リストで別のエントリが作成されます。

![複数の端末](media/integrated-terminal/terminal-multiple-instances.png)

ごみ箱に移動できるボタンを押せばターミナル インスタンスを削除します。

> [!TIP]
> 複数の端末を広範囲に使用する場合は、に対するキー バインドを追加することができます、 `focusNext`、`focusPrevious`と`kill`に記載されているコマンド、[キー バインディング セクション](#key-bindings)キーボードのみを使用してそれらの間を移動できるようにします。

## <a name="configuration"></a>構成

シェルに使用される既定値は`$SHELL`Linux や macOS、Windows 10 での PowerShell と cmd.exe 以前のバージョンの Windows にします。 設定して手動でオーバーライドできます`terminal.integrated.shell.*`で[設定](settings.md)です。 Linux および macOS を使用してターミナル シェルに引数を渡すことができます、`terminal.integrated.shellArgs.*`設定します。

### <a name="windows"></a>Windows

Windows 上のシェルを適切に構成するには右側の実行可能ファイルを特定し、設定を更新します。 共通のシェルの実行可能ファイルとそれら既定の場所の一覧を次に示します。

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
> 統合ターミナルとして使用される、シェルの実行可能ファイルは、コンソール アプリケーションをする必要がありますように`stdin/stdout/stderr`リダイレクトできます。

> [!TIP]
> 権限で実行しているターミナル integrated shell[!INCLUDE[name-sos](../includes/name-sos-short.md)]です。 管理者特権 (管理者) または異なる権限を持つシェル コマンドを実行する必要がある場合、プラットフォームのユーティリティをなど、使用できる`runas.exe`端末内です。

### <a name="shell-arguments"></a>シェル引数

起動するときは、シェルに引数を渡すことができます。

たとえば、ログイン シェルとしての実行中のバッシュを有効にする (実行に使用する`.bash_profile`)、渡す、 `-l` (二重引用符) を含む引数。

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>ターミナル ディスプレイの設定

次の設定では、統合ターミナル フォントと行の高さをカスタマイズできます。

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>ターミナル ショートカット キー

**ビュー: トグル統合ターミナル**にコマンドがバインドされている**Ctrl +'**ビューとの間の統合のターミナル パネルを簡単に切り替えるにします。

統合ターミナル内をすばやく移動するキーボード ショートカットを次に示します。

Key|コマンド
---|---
**Ctrl +'**|統合ターミナルを表示します。
**Ctrl + Shift +'**|新しいターミナルを作成します。
**Ctrl キーを押しながら上**|上にスクロール
**Ctrl キーを押しながら下**|下にスクロール
**Ctrl + pageup**|スクロール pageup
**Ctrl + pagedown**|下へスクロール ページ
**Ctrl + home**|最上部までスクロールします。
**Ctrl キーを押しながら End キー**|一番下までスクロールします。
**Ctrl + K**|ターミナルをクリアします。

他のターミナル コマンドは、使用、好みのキーボード ショートカット キーにバインドすることができます。

これらは次のとおりです。

* `workbench.action.terminal.focus`: 端末の重点を置きます。 これにより、表示/非表示に似ていますが、表示されている場合、非表示にするのではなくターミナル焦点を当てています。
* `workbench.action.terminal.focusNext`: 次のターミナル インスタンス焦点を当てています。
* `workbench.action.terminal.focusPrevious`: 前のターミナル インスタンス焦点を当てています。
* `workbench.action.terminal.kill`: 現在のターミナル インスタンスを削除します。
* `workbench.action.terminal.runSelectedText`: ターミナルのインスタンスで、選択したテキストを実行します。
* `workbench.action.terminal.runActiveFile`: ターミナルのインスタンスでアクティブ ファイルを実行します。

### <a name="run-selected-text"></a>選択したテキストの実行

使用する、`runSelectedText`コマンド、エディターでテキストを選択し、コマンドを実行**ターミナル: アクティブなターミナルで選択されているテキストの実行**を介して、**コマンド パレット**(**Ctrl + Shift + P**). ターミナルは、選択したテキストを実行しようとします。

![選択したテキストを実行します。](media/integrated-terminal/terminal_run_selected.png)

アクティブなエディターでテキストが選択されていない場合、カーソルがある行は、ターミナルで実行されます。

### <a name="copy--paste"></a>コピーと貼り付け

コピーと貼り付けの keybindings は、プラットフォームの標準に従います。

* Linux: **Ctrl + Shift + C**と**ctrl キーと shift キーを押しながら V**
* Mac: **Cmd を押しながら C**と**Cmd を押しながら V**
* Windows: **Ctrl + C**と**ctrl キーを押しながら V**

### <a name="find"></a>[検索]

統合端末がでトリガー可能な基本の検索機能を持つ**Ctrl + F**です。

場合は**Ctrl + F**キーの割り当てを削除する必要が進むには、検索ウィジェットで Linux および Windows を起動せずに、シェルに、次のようにします。

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>ターミナル セッションの名前を変更します。

統合ターミナル セッションここで名前を変更できるを使用して、**ターミナル: 名前を変更**(`workbench.action.terminal.rename`) コマンド。 新しい名前は、ターミナル選択ドロップダウンに表示されます。

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>強制的にターミナルを通過するショートカット キー

統合端末にフォーカスがあるときに、キーストロークに渡され、端末自体によって消費されるため、多くのキー バインドは機能しません。 `terminal.integrated.commandsToSkipShell`これを回避するための設定を使用できます。 キー バインドは、シェルによって処理をスキップし、によって処理される代わりに、コマンド名の配列が含まれている、[!INCLUDE[name-sos](../includes/name-sos-short.md)]バインド システムのキーします。 既定では、select のいくつか一般的に使用されるキー バインドだけでなく、すべてのターミナル キー バインドが含まれます。

