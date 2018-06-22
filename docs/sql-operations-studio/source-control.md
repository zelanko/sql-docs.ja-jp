---
title: ソース SQL Operations Studio (プレビュー) の管理 |Microsoft ドキュメント
description: SQL Operations Studio (プレビュー) でソース管理を構成する方法を説明します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e947bfbd96b5a098728ff423e3eb591544e5f453
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34236433"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>ソース管理での使用 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] バージョン/ソース管理に Git をサポートしています。


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Git のサポート [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Git ソース コントロール マネージャー (SCM) は同梱する必要があります[Git のインストール (version 2.0.0 またはそれ以降)](https://git-scm.com/download)前に、これらの機能を利用できます。 



## <a name="open-an-existing-git-repository"></a>既存の Git リポジトリを開く

1. **ファイル**メニューの下にある、**フォルダーを開く.** を選択します。
2. Gitによって追跡されるファイルを含むフォルダーを参照し、**フォルダーの選択**をクリックします。 ローカル リポジトリ内のサブフォルダーは、ここで選択することができます。


## <a name="initialize-a-new-git-repository"></a>新しい git リポジトリを初期化します。

1. **ソース管理**を選択し、gitアイコンを選択します。


   ![ソース管理の git アイコン](media/source-control/source-control.png)

1. Gitリポジトリとして初期化したいフォルダへのパスを入力し、**Enter**を押します。

   ![Git リポジトリを初期化します。](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Git リポジトリの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)] VS Code からその Git 実装を継承しますが、現在 SCM プロバイダーの追加をサポートしていません。 リポジトリを開く、または初期化した後のGitの操作に関する詳細については、次を参照してください。 [VS コードでの Git サポート](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)


## <a name="additional-resources"></a>その他のリソース
- [Git のドキュメント](https://git-scm.com/documentation)
