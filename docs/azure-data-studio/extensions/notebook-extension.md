---
title: Jupyter Notebook 拡張機能を作成する
description: 拡張機能ジェネレーターを使用してノートブックを拡張機能にパッケージ化する方法について説明します
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: 52a38a8074814737a30cb2f31d22da922eb76901
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288154"
---
# <a name="create-a-jupyter-notebook-extension"></a>Jupyter Notebook 拡張機能を作成する

このチュートリアルでは、新しい Notebooks Azure Data Studio 拡張機能を作成する方法について説明します。 この拡張機能を使用すると、Azure Data Studio で開いて実行できる Jupyter Notebook のサンプルを送信することができます。

このチュートリアルでは、次の方法を学習します。
> [!div class="checklist"]
> - 拡張機能プロジェクトを作成する
> - 拡張機能ジェネレーターをインストールする
> - Notebook 拡張機能を作成する
> - 拡張機能を実行する
> - 拡張機能をパッケージ化する
> - 拡張機能をマーケットプレースに公開する

## <a name="apis-used"></a>使用される API

- `azdata.nb.showNotebookDocument`

### <a name="extension-use-cases"></a>拡張機能のユース ケース

Notebook 拡張機能を作成する理由はいくつかあります。 
- 対話型ドキュメントを共有する 
- そのノートブックを保存して、常にアクセスできるようにする
- ユーザーが理解できるようにコーディングの問題を提示する
- ノートブックの更新のバージョン管理と追跡

## <a name="prerequisites"></a>前提条件

Azure Data Studio は Visual Studio Code と同じフレームワーク上に構築されるため、Azure Data Studio の拡張機能は Visual Studio Code を使用して構築されます。 開始するには、次のコンポーネントが必要です。

- `$PATH` にインストールされ、利用できる [Node.js](https://nodejs.org)。 Node.js には、拡張機能ジェネレーターのインストールに使用される [npm](https://www.npmjs.com/) (Node.js パッケージ マネージャー) が含まれています。
- 拡張機能をデバッグするための [Visual Studio Code](https://code.visualstudio.com)。
- 確実に `azuredatastudio` をパスに含めます。 Windows の場合、setup.exe で `Add to Path` オプションを選択します。 Mac または Linux の場合、*[PATH 内に 'azuredatastudio' コマンドをインストールします]* オプションを実行します。

## <a name="install-the-extension-generator"></a>拡張機能ジェネレーターをインストールする

拡張機能作成のプロセスを簡単にするため、Yeoman を利用して[拡張機能ジェネレーター](https://www.npmjs.com/package/generator-azuredatastudio)を構築しました。 これをインストールするには、コマンド プロンプトから次を実行します。

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-extension"></a>拡張機能を作成する

拡張機能を作成するには: 

1. 次のコマンドを使用して拡張機能ジェネレーターを起動します。

   `yo azuredatastudio`

2. 拡張機能の種類一覧から **[New Notebooks (Individual)]\(新しいノートブック (個別)\)** を選択します。

   :::image type="content" source="media/notebook-extension/notebook-extension-generator.png" alt-text="Notebook 拡張機能ジェネレーター":::

3. 手順に従って、拡張機能名 (このチュートリアルでは **Test Notebook** を使用)、公開元名 (このチュートリアルでは **Microsoft** を使用) を入力し、説明を追加します。

ここにいくつか分岐が存在します。既に作成した Jupyter ノートブックを追加するか、ジェネレーターから提供されるサンプル ノートブックを使用できます。

このチュートリアルでは、サンプルの Python ノートブックを使用します。

   :::image type="content" source="media/notebook-extension/notebook-sample-generator.png" alt-text="Python サンプルを選択する":::

送信したいノートブックがある場合は、送信したい既存のノートブックがあることを答え、すべてのノートブックまたはマークダウン ファイルが存在する絶対ファイル パスを指定します。

以上の手順を完了すると、サンプル ノートブックを含む新しいフォルダーが作成されます。 Visual Studio Code でフォルダーを開くと、新しいノートブック拡張機能を送信する準備が整います。

## <a name="understanding-your-extension"></a>拡張機能の概要

この時点で、プロジェクトは次のように表示されます。

   :::image type="content" source="media/notebook-extension/notebook-file-structure-generator.png" alt-text="拡張機能ファイルの構造":::

`vsc-extension-quickstart.md` には、重要なファイルのリファレンスが用意されています。 `README.md` によって、新しい拡張機能のドキュメントが提供されます。 `package.json`、`notebook.ts`、および `pySample.ipynb` のファイルに注目してください。

公開しないファイルまたはフォルダーがある場合は、その名前を `.vscodeignore` ファイルに含めることができます。

`notebook.ts` を確認して、新しく作成した拡張機能の動作を見てみましょう。

```javascript
// This function is called when you run the command `Launch Notebooks: Test Notebook` from
// command palette in Azure Data Studio. If you would like any additional functionality
// to occur when you launch the book, add to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchNotebooks.test-notebook', () => {
        let notebooksToDisplay: Array<string> = processNotebooks();
        notebooksToDisplay.forEach(name => {
            azdata.nb.showNotebookDocument(vscode.Uri.file(name));
        });
    }));

    // Add other code here if you want to register another command
}
```

これは `notebook.ts` のメイン関数です。これは **[Launch Notebooks: Test Notebook]\(ノートブックの起動: Test Notebook\)** コマンドを使用して拡張機能を実行するたびに呼び出されます。 `vscode.commands.registerCommand` API を使用して新しいコマンドを作成します。中かっこ内の次の定義は、コマンドを呼び出すたびに実行されるコードです。 `processNotebooks` 関数から見つかった各ノートブックについて、`azdata.nb.showNotebookDocument` を使用して Azure Data Studio で開きます。 

`package.json` ファイルは、コマンド **[Launch Notebooks: Test Notebook]\(ノートブックの起動: Test Notebook\)** を登録する場合にも重要な役割を果たします。

```json
"activationEvents": [
        "onCommand:launchNotebooks.test-notebook"
    ],
    "main": "./out/notebook.js",
    "contributes": {
        "commands": [
            {
                "command": "launchNotebooks.test-notebook",
                "title": "Launch Notebooks: Test Notebook"
            }
        ]
    }
```

コマンドのアクティブ化イベントがあり、特定のコントリビューション ポイントも追加されています。 これらは、ユーザーが拡張機能を見ているときに、拡張機能が公開されている拡張機能マーケットプレースに表示されます。 コマンドを追加する場合は、必ず `activationEvents` フィールドに追加してください。 詳細については、「[アクティブ化イベント](https://code.visualstudio.com/api/references/activation-events)」を参照してください。

## <a name="package-your-extension"></a>拡張機能をパッケージ化する

他者と共有するには、拡張機能を 1 つのファイルにパッケージ化する必要があります。 ファイルは Azure Data Studio 拡張機能マーケットプレースに公開するか、チームやコミュニティで共有できます。 それを行うには、別の npm パッケージをコマンド ラインからインストールする必要があります。

```console
`npm install -g vsce`
```

`README.md` を好みに応じて編集し、次に拡張機能のベース ディレクトリに移動して、`vsce package` を実行します。 必要に応じてリポジトリを拡張機能とリンクすることも、それなしで続行することもできます。 1 つ追加するには、`package.json` ファイルに同様の行を追加します。

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testnotebook.git"
}
```

これが完了すると、my test-notebook-0.0.1.vsix ファイルが作成され、インストールして世界中の人と共有する準備が整います。

## <a name="run-your-extension"></a>拡張機能を実行する

拡張機能を実行してテストするには、Azure Data Studio を開き、コマンド パレット (`Ctrl + Shift + P`) を開きます。 コマンド **[Extensions: Install from VSIX]\(拡張機能: VSIX からのインストール\)** を見つけて、新しい拡張機能が格納されているフォルダーに移動します。

   :::image type="content" source="media/notebook-extension/install-vsix.png" alt-text="VSIX のインストール":::

この時点で、Azure Data Studio の拡張機能パネルに表示されます。 コマンド パレットをもう一度開くと、拡張機能を使用して作成した新しいコマンドの **[Launch Book: Test Book]\(ブックの起動: Test Book\)** が表示されます。 実行すると、拡張機能とともにパッケージ化した Jupyter Book が開きます。

   :::image type="content" source="media/notebook-extension/notebook-launch-ads.png" alt-text="Notebook コマンド":::

おめでとうございます! これで、最初の Jupyter Notebook 拡張機能がビルドされ、送信できるようになりました。

## <a name="publish-your-extension-to-the-marketplace"></a>拡張機能をマーケットプレースに公開する

Azure Data Studio 拡張機能マーケットプレースはまだ完全には実装されていません。 公開するには、拡張機能の VSIX をいずれかの場所 (たとえば、GitHub リリース ページ) でホストし、[この JSON ファイル](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json)を拡張機能の情報で更新する PR を送信します。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、以下の内容を学習しました。
> [!div class="checklist"]
> - 拡張機能プロジェクトを作成する
> - 拡張機能ジェネレーターをインストールする - Notebook 拡張機能を作成する
> - 拡張機能を作成する
> - 拡張機能をパッケージ化する
> - 拡張機能をマーケットプレースに公開する

読了後、Azure Data Studio の拡張機能を自分でも作るべく奮起していただけたら幸いです。

アイデアはあるが、どこから始めたらいいのかわからない場合、チーム宛に問題提起またはツイートしてください ([azuredatastudio](https://twitter.com/azuredatastudio))。

[Visual Studio Code 拡張ガイド](https://code.visualstudio.com/docs/extensions/overview)では、既存の API やパターンがすべて取り上げられているので、いつでも参考にできます。