---
title: キーボード ショートカットの作成とカスタマイズ
description: Azure Data Studio でキーボード ショートカットを作成し、カスタマイズする方法について説明します
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: da7ca6132a8727d4ea77b3549f1e4d6199741b3a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774577"
---
# <a name="keyboard-shortcuts-in-azure-data-studio"></a>Azure Data Studio のキーボード ショートカット

この記事では、Azure Data Studio でキーボード ショートカットをすばやく表示、編集、および作成する手順について説明します。

Azure Data Studio のキー バインド機能は Visual Studio Code から継承されているため、高度なカスタマイズや、さまざまなキーボード レイアウトの使用などの詳細については、「[Visual Studio Code のキー バインド](https://code.visualstudio.com/docs/getstarted/keybindings)」を参照してください。 一部のキー バインド機能については使用できない場合があります (たとえば、キーマップ拡張機能は、Azure Data Studio ではサポートされていません)。

## <a name="open-the-keyboard-shortcuts-editor"></a>キーボード ショートカット エディターを開く

現在定義されているキーボード ショートカットをすべて表示するには:

**[ファイル]** メニューから、**キーボード ショートカット** エディターを開きます。 **[ファイル]**  >  **[基本設定]**  >  **[キーボード ショートカット]** (Mac の場合は **[Azure Data Studio]**  >  **[基本設定]**  >  **[キーボード ショートカット]** )。

**キーボード ショートカット** エディターでは、現在のキー バインドを表示することに加えて、キーボード ショートカットが定義されていない使用可能なコマンドの一覧を表示できます。 **キーボード ショートカット** エディターを使用すると、キー バインドの変更、削除、リセット、および新しいキー バインドの定義を簡単に行うことができます。  

## <a name="edit-existing-keyboard-shortcuts"></a>既存のキーボード ショートカットを編集する

既存のキーボード ショートカットのキー バインドを変更するには:

1. 検索ボックスを使用するか、または一覧をスクロールして、変更するキーボード ショートカットを見つけます。
   > [!TIP]
   > キー、コマンド、ソースなどで検索して、関連するすべてのキーボード ショートカットを表示します。

2. 目的のエントリを右クリックし、 **[Change Key binding]\(キー バインドの変更\)** を選択します

   ![キーボード ショートカットを編集する](media/keyboard-shortcuts/change-keybinding.png)

3. 目的のキーの組み合わせを押し、**Enter** キーを押してそれを保存します。 

   ![キーボード ショートカットを保存する](media/keyboard-shortcuts/save-keybinding.png)

## <a name="create-new-keyboard-shortcuts"></a>新しいキーボード ショートカットを作成する

新しいショートカットキーを作成するには:

1. キー バインドが設定されていないコマンドを右クリックし、 **[Add Key binding]\(キー バインドの追加\)** を選択します。

   ![キーボード ショートカットを作成する](media/keyboard-shortcuts/add-keybinding.png)

2. 目的のキーの組み合わせを押し、**Enter** キーを押してそれを保存します。