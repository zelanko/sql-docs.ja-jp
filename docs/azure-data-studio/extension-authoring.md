---
title: Azure Data Studio の拡張機能を作成する |Microsoft Docs
description: Azure データ studio の拡張機能を追加します。
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7d778eb4df52d28a44ec8127ebc9f657a9f0dde
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2018
ms.locfileid: "49355884"
---
# <a name="extend-the-functionality-of-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] の機能を拡張します

[!INCLUDE[name-sos](../includes/name-sos-short.md)] の拡張機能はベース [!INCLUDE[name-sos](../includes/name-sos-short.md)] のインストールにより多くの機能を簡単に追加する方法を提供します。

拡張機能は、サード パーティ コミュニティ (する!) と (マイクロソフト)、Azure Data Studio チームによって提供されます。


## <a name="author-an-extension"></a>拡張機能を作成します。

Azure Data Studio の拡張に知りたい場合は、独自の拡張機能を作成し、拡張機能ギャラリーに発行します。

**拡張機能の記述**

***前提条件***

拡張機能を開発するには、必要があります Node.js インストールして、$PATH で使用できます。 Node.js には、npm、拡張機能ジェネレーターをインストールするために使用する Node.js パッケージ マネージャーが含まれています。

新しい拡張機能を開始するには、Azure データ Studio の拡張機能ジェネレーターを使用することができます。 Yeoman[拡張機能ジェネレーター](https://www.npmjs.com/package/generator-sqlops)簡単な拡張機能プロジェクトを作成する非常に簡単になります。 コード ジェネレーターを起動するには、コマンド プロンプトで、次を入力します。

`npm install -g yo generator-sqlops`

`yo sqlops`


**拡張機能の参照**

Azure データ Studio 機能拡張を参照してください詳細については[機能拡張の概要](extensibility.md)します。 既存の API を使用する方法の例を確認できます[サンプル](https://github.com/Microsoft/azuredatastudio/tree/master/samples)します。


## <a name="debug-an-extension"></a>拡張機能をデバッグします。

Visual Studio Code 拡張機能を使用して新しい拡張機能をデバッグする[Azure データ Studio はデバッグ](https://github.com/kevcunnane/sqlops-debug)します。

手順
- 拡張機能を開く[Visual Studio Code](https://code.visualstudio.com/)
- Azure データ Studio のデバッグ拡張機能をインストールします。
- キーを押して**F5**デバッグ アイコンをクリックし、をクリックしてまたは**開始**します。
- 特殊なモード (拡張機能開発ホスト) で Azure Data Studio の新しいインスタンスを起動し、この新しいインスタンスを拡張機能を意識なります。


## <a name="create-an-extension-package"></a>拡張機能パッケージを作成します。

拡張機能を作成した後は、Azure Data Studio にインストールすることができる VSIX パッケージを作成する必要があります。 使用することができます[vsce](https://github.com/Microsoft/vscode-vsce) VSIX パッケージを作成します。

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>拡張機能を公開します。

Azure Data Studio に新しい拡張機能を発行します。

1. 拡張機能を追加します。 https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json
2. 現在ホスト サード パーティ製の拡張機能のサポートがないため、Azure Data Studio、拡張機能をダウンロードする代わりに、ダウンロード ページを参照するオプションがあります。 拡張機能のダウンロード ページを設定するには、資産"Microsoft.AzureDataStudio.DownloadPage"の値を設定します。
3. リリース/拡張機能ブランチに対してプル要求を作成します。
4. チームにレビューの要求を送信します。

拡張機能の見直しし、拡張機能ギャラリーに追加します。

**拡張機能の更新の発行**更新プログラムを公開するプロセスは拡張機能を公開に似ています。 Package.json でバージョンが更新を確認してください。
