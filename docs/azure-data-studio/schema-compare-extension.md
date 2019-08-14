---
title: スキーマ比較の拡張機能
titleSuffix: Azure Data Studio
description: Azure Data Studio 用のスキーマ比較の拡張機能 (プレビュー) をインストールして使用します
ms.custom: seodec18
ms.date: 06/06/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a51d64202d3d906b3106092084628b0a961297ea
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959324"
---
# <a name="schema-compare-extension-preview"></a>スキーマ比較の拡張機能 (プレビュー)
スキーマ比較の拡張機能により、.dacpac ファイルやデータベースを比較し、ソースからターゲットに変更を適用するための使いやすいエクスペリエンスが提供されます。

このエクスペリエンスは、現在、初期のプレビュー段階にあります。 問題の報告や機能の要求を行うには、[ここ](https://github.com/microsoft/azuredatastudio/issues)にアクセスしてください。

## <a name="install-the-schema-compare-extension"></a>スキーマ比較の拡張機能のインストール

1. 拡張機能マネージャーを開いて、使用可能な拡張機能にアクセスするには、拡張機能アイコンを選択するか、 **[表示]** メニューの **[拡張機能]** を選択します。
2. 使用可能な拡張機能を選択すると、その詳細が表示されます。
1. 必要な拡張機能 (スキーマ比較) を選択して**インストール**します。

## <a name="how-do-i-start-a-schema-comparison"></a>スキーマ比較を開始する方法
* スキーマ比較のメインのエントリ ポイントは、オブジェクト エクスプローラーでデータベースを右クリックして、 **[スキーマ比較]** をクリックすることです。
* ユーザーは、**スキーマ比較**を検索して、コマンド パレット (Ctrl + Shift + P) から [スキーマ比較] ダイアログを起動することもできます。

## <a name="why-would-i-use-the-schema-compare"></a>スキーマ比較を使用する理由
スキーマ比較は、.dacpac ファイルとデータベースのスキーマを比較して変更を適用する機能を追加するために作成されました。

## <a name="next-steps"></a>次の手順
スキーマ比較の詳細については、[Microsoft のドキュメントを参照してください。](https://docs.microsoft.com/sql/ssdt/how-to-use-schema-compare-to-compare-different-database-definitions)


