---
title: チュートリアル:拡張機能を作成する
titleSuffix: Azure Data Studio
description: このチュートリアルでは、Azure Data Studio にカスタム機能を追加する拡張機能を作成する方法を示します。
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: kevcunnane
ms.author: kcunnane
manager: craigg
ms.openlocfilehash: 0a4e877a91cad978bb62747bd50e40adaa69ef1c
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030606"
---
# <a name="tutorial-create-an-azure-data-studio-extension"></a>チュートリアル:Azure Data Studio の拡張機能を作成します。

このチュートリアルでは、Azure Data Studio の新しい拡張機能を作成する方法を示します。 拡張機能は、Azure Data Studio で、SSMS の使い慣れたキー バインドを作成します。

このチュートリアルの中に確認する方法。
> [!div class="checklist"]
> * 拡張機能プロジェクトを作成します。
> * 拡張機能ジェネレーターをインストールします。
> * 拡張機能を作成します。
> * 拡張機能をテストします。
> * 拡張機能をパッケージ化します。
> * 拡張機能を marketplace に公開します。

## <a name="prerequisites"></a>前提条件

Azure Data Studio は、Visual Studio Code を使用して Azure Data Studio の拡張機能が組み込まれているように、Visual Studio Code と同じフレームワークに基づいて構築されます。 開始するには、次のコンポーネントが必要です。

- [Node.js](https://nodejs.org)インストールされで使用できる、`$PATH`します。 Node.js を含む[npm](https://www.npmjs.com/)、拡張機能ジェネレーターをインストールするために使用する Node.js パッケージ マネージャー。
- [Visual Studio Code](https://code.visualstudio.com)拡張機能をデバッグします。
- Azure の Data Studio[拡張機能をデバッグ](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug)します。
- 確認`sqlops`がパスにします。 、Windows のことを選択することを確認して、 `Add to Path` setup.exe オプション。 Mac または Linux の場合は、実行、 *'sqlops' コマンドのインストール パスで*オプション。
- SQL Operations Studio のデバッグ拡張機能 (省略可能)。 これにより、パッケージ化し、Azure Data Studio にインストールすることがなく、拡張機能をテストできます。


## <a name="install-the-extension-generator"></a>拡張機能ジェネレーターをインストールします。

拡張機能の作成のプロセスを簡素化するために構築した、[拡張機能ジェネレーター](https://code.visualstudio.com/docs/extensions/yocode) Yeoman を使用します。 これをインストールするには、コマンド プロンプトから、次を実行します。

`npm install -g yo generator-sqlops`

## <a name="create-your-extension"></a>拡張機能を作成します。

拡張機能を作成します。

1. 次のコマンドを使用して拡張機能ジェネレーターを起動します。

   `yo sqlops`

2. 選択**新しいキーマップ**拡張機能の種類の一覧から。

   ![拡張機能ジェネレーター](./media/tutorial-create-extension/extension-generator.png)

3. 拡張機能の名前を入力する手順に従います (このチュートリアルでは、使用**ssmskeymap**)、および説明を追加します。

前の手順を完了するには、新規のフォルダーが作成されます。 開いている Visual Studio Code でフォルダーができました、独自のキー バインド拡張機能を作成します。


### <a name="add-a-keyboard-shortcut"></a>キーボード ショートカットを追加します。

**ステップ 1: 置換するショートカットを検索します。**

準備が整ったら、拡張機能をしたら、いくつか SSMS キーボード ショートカット (またはキー バインド) Azure Data Studio を追加します。 使用して[Andy Mallon のチートシート](https://am2.co/2018/02/updated-cheat-sheet/)とインスピレーションを RedGate のキーボード ショートカットの一覧。

見た、不足している上位のものは次のとおりです。

- 有効になっている実際の実行プランでは、クエリを実行します。 これは**Ctrl + M** SSMS で Azure Data Studio にバインディングを持っていないとします。
- ある**CTRL + SHIFT + E**のクエリを実行する 2 番目の方法として。 ユーザーからのフィードバックでは、これが不足していることを示しています。
- ある**alt+f1**実行`sp_help`します。 Azure Data Studio でこれを追加しましたにマップした後、そのバインドが既に使用されて、 **ALT + F2**代わりにします。
- 全画面表示の切り替え (**SHIFT + ALT + ENTER**)。
- **F8**を表示する**オブジェクト エクスプ ローラー** / **サーバー 表示で**します。

検索し、置換のこれらのキー バインドを簡単になります。 実行*オープンのキーボード ショートカット*を表示する、**のキーボード ショートカット**で Azure Data Studio タブで、検索*クエリ*選び、**バインドのキーの変更**. 完了したら、キーの割り当てを変更するには、keybindings.json ファイルで更新されるマッピングを表示できます (実行*オープンのキーボード ショートカット*を確認する)。

![キーボード ショートカット](./media/tutorial-create-extension/keyboard-shortcuts.png)

![keybindings.json 拡張機能](./media/tutorial-create-extension/keybindings-json.png)


**手順 2:拡張機能のショートカットを追加します。**

拡張機能には、ショートカットを追加するには、開く、 *package.json* (拡張機能) でファイルを開き、`contributes`を次のセクション。

```json
"contributes": {
  "keybindings": [
    {
      "key": "shift+cmd+e",
      "command": "runQueryKeyboardAction"
    },
    {
      "key": "ctrl+cmd+e",
      "command": "workbench.view.explorer"
    },
    {
      "key": "alt+f1",
      "command": "workbench.action.query.shortcut1"
    },
    {
      "key": "shift+alt+enter",
      "command": "workbench.action.toggleFullScreen"
    },
    {
      "key": "f8",
      "command": "workbench.view.connections"
    },
    {
      "key": "ctrl+m",
      "command": "runCurrentQueryWithActualPlanKeyboardAction"
    }
  ]
}
```

## <a name="test-your-extension"></a>拡張機能をテストします。

確認`azuredatastudio`がパスに Azure Data Studio での PATH コマンドでインストールの azuredatastudio コマンドを実行します。

Visual Studio Code で Azure Data Studio のデバッグ拡張機能がインストールされていることを確認します。

選択**F5**デバッグ モードで実行されている拡張機能で Azure Data Studio を起動します。

![拡張機能をインストールします。](./media/tutorial-create-extension/install-extension.png)

![拡張機能をテストします。](./media/tutorial-create-extension/test-extension.png)

キー マップでは、新しい拡張機能が正常に機能し、共有できるようになりますのでを作成する最も簡単な拡張機能の 1 つです。

## <a name="package-your-extension"></a>拡張機能をパッケージ化します。

他のユーザーと共有するには、1 つのファイルに、拡張機能をパッケージ化する必要があります。 これは、Azure Data Studio の拡張機能マーケットプ レースに発行できます。 またはチームまたはコミュニティの間で共有します。 これを行うには、コマンドラインから別の npm パッケージをインストールする必要があります。

`npm install -g vsce`

の拡張機能の基本ディレクトリに移動し、実行`vsce package`します。 余分な行を停止するをいくつか追加する必要がある、 *vsce*から不平ツール。

```json
"repository": {
    "type": "git",
    "url": "https://github.com/kevcunnane/ssmskeymap.git"
},
"bugs": {
    "url": "https://github.com/kevcunnane/ssmskeymap/issues"
},
```

これは、いったん ssmskeymap 0.1.0.vsix ファイルは作成され、インストールして、世界中で共有するでした。

![拡張機能をインストールします。](./media/tutorial-create-extension/extensions.png)


## <a name="publish-your-extension-to-the-marketplace"></a>拡張機能を marketplace に公開します。

Azure Data Studio の拡張機能マーケットプ レースは完全にまだ実装されていないが、現在のプロセスがどこかに VSIX (たとえば、GitHub のリリース ページ) 拡張機能をホストする、送信、PR の更新[この JSON ファイル](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json)で、拡張機能の情報です。


## <a name="next-steps"></a>次の手順

このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * 拡張機能プロジェクトを作成します。
> * 拡張機能ジェネレーターをインストールします。
> * 拡張機能を作成します。
> * 拡張機能をテストします。
> * 拡張機能をパッケージ化します。
> * 拡張機能を marketplace に公開します。


Azure Data Studio の独自の拡張機能をビルドひらめくこれを読んでいることと思います。 ダッシュ ボード Insights (SQL Server に対して実行されるきれいなグラフ)、複数の SQL 固有の Api を Visual Studio Code から継承された拡張ポイントの既存の巨大なセットのサポートがあります。

問題や、チームでツイート開いてくださいアイデアが開始する方法がわからない場合: [azuredatastudio](https://twitter.com/azuredatastudio)します。

常に参照することができます、 [Visual Studio Code 拡張機能のガイド](https://code.visualstudio.com/docs/extensions/overview)のため、すべての既存の Api とパターンについて説明します。


Azure Data Studio で T-SQL を使用する方法については、するには、T-SQL エディターのチュートリアルを行います。

> [!div class="nextstepaction"]
> [TRANSACT-SQL エディターを使用して、データベース オブジェクトを作成する](tutorial-sql-editor.md)します。
