---
title: Azure Data Studio のノートブックと Python カーネル
description: このチュートリアルでは、Python ノートブックを作成し、実行する方法について説明します。
author: garyericson
ms.author: garye
ms.reviewer: mikeray, alayu, maghan
ms.topic: tutorial
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: 8d0666c74f464535d2de08dd44e92c521cfcd73f
ms.sourcegitcommit: 4f4ca7075a73a7a4d7196dcb279c58e15c2daf37
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196794"
---
# <a name="create-and-run-a-python-notebook"></a>Python ノートブックを作成して実行する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、Python カーネルを使用して、Azure Data Studio でノートブックを作成し、実行する方法について説明します。

## <a name="prerequisites"></a>前提条件

- [Azure Data Studio をインストールしていること](download-azure-data-studio.md)

## <a name="new-notebook"></a>新しいノートブック

次の手順では、Azure Data Studio でノートブック ファイルを作成する方法を示しています。

1. Azure Data Studio を開きます。 SQL Server に接続するかどうかを確認するメッセージが表示されたら、接続するか、 **[キャンセル]** をクリックします。

1. **[ファイル]** メニューで **[新しいノートブック]** を選択します。

1. **[カーネル]** で **[Python 3]** を選択します。

   :::image type="content" source="media/notebook-tutorial-python/set-kernel-and-attach-to-python.png" alt-text="カーネルを設定する":::

1. Python を構成するように求めるメッセージが表示されたら、 **[ノートブック用 Python の構成]** で次のいずれかの操作を行います。

   - **[新しい Python インストール]** を選択して、Azure Data Studio 用の Python の新しいコピーをインストールする
   - **[既存の Python インストールを使用する]** を選択して、既存の Python インストールのパスを指定する

## <a name="run-a-notebook-cell"></a>ノートブック セルを実行する

コードまたはテキストを含むセルを作成できます。 作成したコード セルは実行することができ、セルの実行が完了すると、結果がノートブックに表示されます。 テキスト セルを使用すると、書式設定されたドキュメントにコードを配置することができます。

### <a name="code"></a>コード

ツールバーの **[+Code]** コマンドを選択して、新しい Python コード セルを追加します。

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python.png" alt-text="ノートブック ツール バー":::

この例では、単純な数値演算を実行します。

```python
a = 1
b = 2
c = a/b
print(c)
```
セルの左側にある再生ボタンをクリックして、セルを実行します。 結果は下部に表示されます。

:::image type="content" source="media/notebook-tutorial-python/run-notebook-cell-python.png" alt-text="ノートブック セルを実行する":::

### <a name="text"></a>Text

ツールバーの **[+Text]** コマンドを選択して、新しいテキスト セルを追加します。

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python-text.png" alt-text="ノートブック ツール バー":::

セルは編集モードに変わり、マークダウンを入力できるようになります。入力すると、プレビューも同時に表示されます。

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-cell-python.png" alt-text="マークダウン セル":::

テキスト セルの外側を選択すると、マークダウン テキストだけが表示されます。

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-preview-python.png" alt-text="マークダウン テキスト":::

## <a name="next-steps"></a>次のステップ

ノートブックについてさらに学習します:

- [SQL Server でノートブックを使用する方法](notebooks-guidance.md)

- [SQL Server ノートブックを作成して実行する](notebooks-tutorial-sql-kernel.md)

- [Azure Data Studio でノートブックを管理する方法](notebooks-manage-sql-server.md)
