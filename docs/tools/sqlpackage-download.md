---
title: ダウンロードしてインストール sqlpackage |Microsoft Docs
description: ダウンロードし、Windows、macOS、または Linux の sqlpackage のインストール
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sqlpackage
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: fa682766fe4330a34cff39600b6296403031a3e4
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080040"
---
# <a name="download-and-install-sqlpackage"></a>ダウンロードしてインストール sqlpackage

sqlpackage は、Windows、macOS、Linux で実行されます。

ダウンロードして、最新の .NET Framework リリースおよび macOS と Linux のプレビューをインストールします。

|プラットフォーム|ダウンロード|リリース日|[バージョンのオプション]|ビルド|
|:---|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=875508)|2018 年 6 月 22 日|17.8|14.0.4079.2|
|macOS (プレビュー)|[.zip](https://go.microsoft.com/fwlink/?linkid=873927)|2018 年 5 月 9 日 |0.0.1|15.0.4057.1|
|Linux (プレビュー)|[.zip](https://go.microsoft.com/fwlink/?linkid=873926)|2018 年 5 月 9 日 |0.0.1|15.0.4057.1|

最新リリースに関する詳細については、次を参照してください。、[リリース ノート](sqlpackage-release-notes.md)します。

## <a name="get-sqlpackage-for-windows"></a>Windows の sqlpackage を取得します。

Sqlpackage のこのリリースには、標準の Windows インストーラー エクスペリエンスと、.zip が含まれています。 

1. ダウンロードし、実行、 [DacFramework.msi インストーラーは、Windows を](https://go.microsoft.com/fwlink/?linkid=875508)します。
2. 新しいコマンド プロンプト ウィンドウを開き、sqlpackage.exe の実行
    - sqlpackage にインストールされている、```C:\Program Files\Microsoft SQL Server\140\DAC\bin```フォルダー

## <a name="get-sqlpackage-preview-for-macos"></a>MacOS の sqlpackage (プレビュー) を取得します。

1. ダウンロード[macOS 用の sqlpackage](https://go.microsoft.com/fwlink/?linkid=873927)します。
2. ファイルを抽出して、sqlpackage の起動、新しいターミナル ウィンドウを開き、次のコマンドを入力します。

   **.zip のインストール:**

   ```bash
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Linux の sqlpackage (プレビュー) を取得します。

1. ダウンロード[for Linux sqlpackage](https://go.microsoft.com/fwlink/?linkid=873926)インストーラーまたは tar.gz アーカイブのいずれかを使用しています。
2. ファイルを抽出して、sqlpackage の起動、新しいターミナル ウィンドウを開き、次のコマンドを入力します。

   **.zip のインストール:**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bashrc
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > Debian、red Hat、Ubuntu では、依存関係が不足しているがあります。 Linux のバージョンによってこれらの依存関係をインストールするのにには、次のコマンドを使用します。

   **Debian:**

   ```bash
   sudo apt-get install libuwind8
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

## <a name="uninstall-sqlpackage-preview"></a>Sqlpackage (プレビュー) のアンインストールします。

Sqlpackage の Windows インストーラーを使用してをインストールした場合は、任意の Windows アプリケーションを削除するのと同じ方法をアンインストールします。

.Zip、またはその他のアーカイブを sqlpackage をインストールした場合は、ファイルを削除し、だけです。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

sqlpackage は、Windows、macOS、および Linux で実行し、次のプラットフォームでサポートされています。

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

- 詳細については[sqlpackage](sqlpackage.md)

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)