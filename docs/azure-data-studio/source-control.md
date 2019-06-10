---
title: ソース管理
titleSuffix: Azure Data Studio
description: Azure Data Studio でソース管理を構成する方法について説明します
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 6431b869af8abc91a9de319f32c0576b82428a0a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798028"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>ソース管理での使用 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] バージョン/ソース管理に Git をサポートしています。


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Git のサポート [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Git ソース管理マネージャー (SCM) が付属する必要があります[Git のインストール (バージョン 2.0.0 以降)](https://git-scm.com/download)これらの機能ができるようになります。 



## <a name="open-an-existing-git-repository"></a>既存の Git リポジトリを開く

1. **ファイル**メニューの下にある、**フォルダーを開く.** を選択します。
2. Gitによって追跡されるファイルを含むフォルダーを参照し、**フォルダーの選択**をクリックします。 ローカル リポジトリ内のサブフォルダーは、ここで選択することができます。


## <a name="initialize-a-new-git-repository"></a>新しい git リポジトリを初期化します。

1. **ソース管理**を選択し、gitアイコンを選択します。

   ![ソース管理 git アイコン](media/source-control/source-control.png)

1. Gitリポジトリとして初期化したいフォルダへのパスを入力し、**Enter**を押します。

   ![Git リポジトリを初期化します。](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Git リポジトリの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)] VS Code からその Git 実装を継承しますが、現在 SCM プロバイダーの追加をサポートしていません。 リポジトリを開く、または初期化した後のGitの操作に関する詳細については、次を参照してください。 [VS コードでの Git サポート](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)


## <a name="additional-resources"></a>その他のリソース
- [Git に関するドキュメント](https://git-scm.com/documentation)
