---
title: ソース SQL 操作 Studio (プレビュー) の管理 |Microsoft ドキュメント
description: SQL 操作 Studio (プレビュー) でソース管理を構成する方法を説明します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 58475a1c7bfb27f29c1e040de286c82d9c7a204f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>ソース管理での使用 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] バージョン/ソース管理に Git をサポートしています。


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Git のサポート [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Git ソース コントロール マネージャー (SCM) は同梱する必要があります[Git のインストール (version 2.0.0 またはそれ以降)](https://git-scm.com/download)前に、これらの機能を利用できます。 



## <a name="open-an-existing-git-repository"></a>既存の Git リポジトリを開く

1. 下にある、**ファイル**メニューの **フォルダーを開く.**
2. Git、によって追跡ファイルを含むフォルダーを参照してクリックして**フォルダーの選択**です。 ローカル リポジトリ内のサブフォルダーは、ここで選択を使用できます。


## <a name="initialize-a-new-git-repository"></a>新しい git リポジトリを初期化します。

1. 選択**ソース管理**、git アイコンを選択します。

   ![ソース管理の git アイコン](media/source-control/source-control.png)

1. Git リポジトリおよびキーを押してとして初期化するフォルダーへのパスを入力**Enter**です。

   ![Git リポジトリを初期化します。](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Git リポジトリの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)] VS Code からその Git 実装を継承しますが、現在 SCM プロバイダーの追加をサポートしていません。 開くまたはリポジトリを初期化した後、Git の操作に関する詳細については、次を参照してください。 [VS コードでの Git サポート](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)です。


## <a name="additional-resources"></a>その他のリソース
- [Git のドキュメント](https://git-scm.com/documentation)
