---
title: sqlpackage をダウンロードしてインストールする
description: Windows、macOS、または Linux 用の sqlpackage をダウンロードしてインストールします
ms.custom: tools|sos
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
ms.reviewer: alayu; sstein
ms.date: 06/20/2018
ms.openlocfilehash: ed2292c2f2a5fe067b5602ffcf46d52ca93c2f08
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262019"
---
# <a name="download-and-install-sqlpackage"></a>sqlpackage をダウンロードしてインストールする

sqlpackage は Windows、macOS、Linux 上で実行されます。

.NET Framework の最新リリースと、macOS および Linux のプレビューをダウンロードしてインストールします。

|プラットフォーム|ダウンロード|リリース日|Version|Build
|:---|:---|:---|:---|:---|
|Windows|[MSI インストーラー](https://go.microsoft.com/fwlink/?linkid=2128142)|2020 年 4 月 28 日|18.5|15.0.4769.1|
|macOS .NET Core |[zip ファイル](https://go.microsoft.com/fwlink/?linkid=2128145)|2020 年 4 月 28 日| 18.5|15.0.4769.1|
|Linux .NET Core |[zip ファイル](https://go.microsoft.com/fwlink/?linkid=2128144)|2020 年 4 月 28 日| 18.5|15.0.4769.1|
|Windows .NET Core |[zip ファイル](https://go.microsoft.com/fwlink/?linkid=2128143)|2020 年 4 月 28 日| 18.5|15.0.4769.1|

最新リリースに関する詳細については、[リリース ノート](release-notes-sqlpackage.md)をご覧ください。 追加の言語をダウンロードするには、「[使用できる言語](#available-languages)」を参照してください。

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Windows 用の sqlpackage を取得する

このリリースの sqlpackage には、標準の Windows インストーラーのエクスペリエンスと、.zip が含まれています。 

1. [Windows 用の DacFramework.msi インストーラー](https://go.microsoft.com/fwlink/?linkid=2128142)をダウンロードして実行します。
2. 新しいコマンド プロンプト ウィンドウを開き、sqlpackage.exe を実行します
    - sqlpackage は ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` フォルダーにインストールされます

## <a name="get-sqlpackage-net-core-for-windows"></a>Windows 用の sqlpackage .NET Core を取得する

1. [Windows 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=2128143) をダウンロードします。
2. ファイルを抽出するには、エクスプローラーでファイルを右クリックして [すべて展開...] を選択し、ターゲット ディレクトリを選択します。
3. 新しいターミナル ウィンドウを開き、sqlpackage が抽出された場所へ cd を実行します。

   ```cmd
   > sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-macos"></a>macOS 用の sqlpackage .NET Core を取得する

1. [macOS 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=2128145) をダウンロードします。
2. ファイルを抽出して sqlpackage を起動するには、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   ```bash
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   $ echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   $ source ~/.bash_profile
   $ sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-linux"></a>Linux 用の sqlpackage .NET Core を取得する

1. インストーラーのいずれか、または tar.gz アーカイブを使って、[Linux 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=2128144) をダウンロードします。
2. ファイルを抽出して sqlpackage を起動するには、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   ```bash
   cd ~
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   $ echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   $ chmod a+x ~/sqlpackage/sqlpackage
   $ source ~/.bashrc
   $ sqlpackage
   ```

   > [!NOTE]
   > Debian、Redhat、および Ubuntu では、依存関係が不足する場合があります。 ご自身の Linux のバージョンに応じて、次のコマンドを使ってこれらの依存関係をインストールします。

   **Debian:**

   ```bash
   $ sudo apt-get install libunwind8
   ```

   **Redhat:**

   ```bash
   $ yum install libunwind
   $ yum install libicu
   ```

   **Ubuntu:**

   ```bash
   $ sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   $ sudo apt-get install libicu52      # for 14.x
   $ sudo apt-get install libicu55      # for 16.x
   $ sudo apt-get install libicu57      # for 17.x
   $ sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>sqlpackage のアンインストール (プレビュー)

Windows インストーラーを使って sqlpackage をインストールした場合は、Windows アプリケーションを削除するのと同じ方法でアンインストールします。

.zip やその他のアーカイブを使って sqlpackage をインストールした場合は、そのファイルを削除します。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

sqlpackage は、Windows、macOS、および Linux 上で実行されます。また、次のプラットフォーム上でサポートされています。

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 7 SP1
- Windows Server 2008 R2
- Windows Server 2012 R2
- Windows Server 2016

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="available-languages"></a>使用できる言語

sqlpackage の今回のリリースは、次の言語でインストールできます。

sqlpackage Windows:  
[簡体中国語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x40a)

sqlpackage .NET Core Windows:  
[簡体中国語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x40a)

sqlpackage .NET Core macOS:  
[簡体中国語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x40a)

sqlpackage .NET Core Linux:  
[簡体中国語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x40a)

## <a name="next-steps"></a>次の手順

- [sqlpackage](sqlpackage.md) について詳しく学習する

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
