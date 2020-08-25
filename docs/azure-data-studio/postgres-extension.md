---
title: PostgreSQL の拡張機能 (プレビュー)
description: Postgres データベースに接続し、クエリを実行し、開発することを可能にする Azure Data Studio PostgreSQL 拡張機能をインストールする方法について説明します。
ms.custom: seodec18
ms.date: 03/19/2019
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: rachel-msft
ms.author: raagyema
ms.openlocfilehash: ac218ec447ef338b4df770e9251e6fdb37e5db5f
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766641"
---
# <a name="postgresql-extension-preview"></a>PostgreSQL の拡張機能 (プレビュー)

PostgreSQL 拡張機能 (プレビュー) を使用すると、Azure Data Studio の機能を使用して Postgres に接続し、クエリを実行し、開発を行うことができます。 

PostgreSQL で使用できる Azure Data Studio 機能には次のものがあります。

- 接続マネージャーとクエリ エディター
- カスタマイズ可能なダッシュボードと分析情報ウィジェット
- コード スニペット
- [統合ターミナル](integrated-terminal.md)
- [キーボード ショートカット](keyboard-shortcuts.md)
- [ソース管理の統合](source-control.md)
- [ワークスペースとユーザー設定](settings.md)


## <a name="install-the-postgresql-extension-preview"></a>PostgreSQL の拡張機能 (プレビュー) をインストールする

Azure Data Studio がまだインストールされていない場合は、その[インストール手順](./download-azure-data-studio.md?view=sql-server-ver15)を参照してください。

1. Azure Data Studio のサイドバーから拡張機能アイコンを選択します。
   ![拡張機能アイコン](media/extensions/postgresql-extension/extensions-icon.png)

2. 検索バーに「postgresql」と入力します。 PostgreSQL の拡張機能を選択します。

3. **[インストール]** を選択します。 インストールが完了したら、 **[再読み込み]** を選択して Azure Data Studio で拡張機能をアクティブにします。


## <a name="next-steps"></a>次のステップ

[Azure Data Studio から Postgres に接続してクエリを実行する方法](quickstart-postgres.md)について説明します。