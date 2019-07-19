---
title: スキーマ比較の拡張機能
titleSuffix: Azure Data Studio
description: インストールして Azure Data Studio のスキーマ比較拡張機能 (プレビュー) を使用します。
ms.custom: seodec18
ms.date: 06/06/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a51d64202d3d906b3106092084628b0a961297ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959324"
---
# <a name="schema-compare-extension-preview"></a>スキーマ比較の拡張機能 (プレビュー)
スキーマ比較の拡張機能には、.dacpac ファイルやデータベースを比較し、ソースからターゲットに変更を適用する使いやすいエクスペリエンスが提供されます。

このエクスペリエンスは、初期のプレビューは現在です。 問題の報告や機能要求[ここです。](https://github.com/microsoft/azuredatastudio/issues)

## <a name="install-the-schema-compare-extension"></a>スキーマ比較の拡張機能をインストールします。

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. 詳細を表示する使用可能な拡張機能を選択します。
1. (スキーマの比較) が必要な拡張機能を選択し、**インストール**こと。

## <a name="how-do-i-start-a-schema-comparison"></a>スキーマ比較を起動する方法はありますか
* スキーマ比較のメイン エントリ ポイントは、オブジェクト エクスプ ローラーでデータベースを右クリックして **スキーマ比較**します。
* ユーザーを検索してコマンド パレット (Ctrl + Shift + P) から [スキーマ比較] ダイアログを起動できますも**スキーマ比較**

## <a name="why-would-i-use-the-schema-compare"></a>使用する理由、スキーマを比較しますか。
スキーマ比較は、.dacpac ファイルやデータベースからスキーマを比較し、変更を適用する機能を追加作成されました。

## <a name="next-steps"></a>次の手順
スキーマ比較の詳細について[ドキュメントを確認します。](https://docs.microsoft.com/sql/ssdt/how-to-use-schema-compare-to-compare-different-database-definitions)


