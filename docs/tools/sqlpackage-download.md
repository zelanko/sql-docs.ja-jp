---
title: sqlpackage をダウンロードしてインストールする | Microsoft Docs
description: Windows、macOS、または Linux 用の sqlpackage をダウンロードしてインストールします
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
ms.openlocfilehash: d8422146e3569ff991ef16179e54f0f78961fc79
ms.sourcegitcommit: 6413b7495313830ad1ae5aefe0c09e8e7a284b07
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "71016867"
---
# <a name="download-and-install-sqlpackage"></a>sqlpackage をダウンロードしてインストールする

sqlpackage は Windows、macOS、Linux 上で実行されます。

.NET Framework の最新リリースと、macOS および Linux のプレビューをダウンロードしてインストールします。

|プラットフォーム|ダウンロード|リリース日|Version|ビルド
|:---|:---|:---|:---|:---|
|Windows|[MSI インストーラー](https://go.microsoft.com/fwlink/?linkid=2102893)|2019 年 9 月 13 日|18.3.1|15.0.4538.1|
|macOS .NET Core (プレビュー)|[zip ファイル](https://go.microsoft.com/fwlink/?linkid=2102894)|2019 年 9 月 13 日| 18.3.1|15.0.4538.1|
|Linux .NET Core (プレビュー)|[zip ファイル](https://go.microsoft.com/fwlink/?linkid=2102978)|2019 年 9 月 13 日| 18.3.1|15.0.4538.1|
|Windows .NET Core (プレビュー)|[zip ファイル](https://go.microsoft.com/fwlink/?linkid=2102979)|2019 年 9 月 13 日| 18.3.1|15.0.4538.1|

最新リリースに関する詳細については、[リリース ノート](release-notes-sqlpackage.md)をご覧ください。

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Windows 用の sqlpackage を取得する

このリリースの sqlpackage には、標準の Windows インストーラーのエクスペリエンスと、.zip が含まれています。 

1. [Windows 用の DacFramework.msi インストーラー](https://go.microsoft.com/fwlink/?linkid=2102893)をダウンロードして実行します。
2. 新しいコマンド プロンプト ウィンドウを開き、sqlpackage.exe を実行します
    - sqlpackage は ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` フォルダーにインストールされます
    - x86 バージョンを x64 マシンにインストールする場合、sqlpackage は ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin``` フォルダーにインストールされます

## <a name="get-sqlpackage-net-core-preview-for-windows"></a>Windows 用 sqlpackage .NET Core (プレビュー) を取得する

1. [Windows 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=2102979) をダウンロードします。
2. エクスプローラーでファイルを右クリックして [すべて展開...] を選択し、ターゲットディレクトリを選択して、ファイルを抽出します。
3. 新しいターミナルウィンドウを開き、sqlpackage が抽出された場所まで cd を開きます。

   **.zip のインストール:**

   ```bash
   sqlpackage
   ```

## <a name="get-sqlpackage-net-core-preview-for-macos"></a>MacOS 用 sqlpackage .NET Core (プレビュー) を取得する

1. [macOS 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=2102894) をダウンロードします。
2. ファイルを抽出して sqlpackage を起動するには、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   **.zip のインストール:**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-net-core-preview-for-linux"></a>Linux 用 sqlpackage .NET Core (プレビュー) を取得する

1. インストーラーのいずれか、または tar.gz アーカイブを使って、[Linux 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=2102978) をダウンロードします。
2. ファイルを抽出して sqlpackage を起動するには、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   **.zip のインストール:**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   chmod a+x ~/sqlpackage/sqlpackage
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > Debian、Redhat、および Ubuntu では、依存関係が不足する場合があります。 ご自身の Linux のバージョンに応じて、次のコマンドを使ってこれらの依存関係をインストールします。

   **Debian:**

   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:**

   ```bash
   yum install libunwind
   yum install libicu
   ```

   **Ubuntu:**

   ```bash
   sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   sudo apt-get install libicu52      # for 14.x
   sudo apt-get install libicu55      # for 16.x
   sudo apt-get install libicu57      # for 17.x
   sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>sqlpackage のアンインストール (プレビュー)

Windows インストーラーを使って sqlpackage をインストールした場合は、Windows アプリケーションを削除するのと同じ方法でアンインストールします。

.zip やその他のアーカイブを使って sqlpackage をインストールした場合は、単にファイルを削除します。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

sqlpackage は、Windows、macOS、および Linux 上で実行されます。また、次のプラットフォーム上でサポートされています。

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- [sqlpackage](sqlpackage.md) について詳しく学習する

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
