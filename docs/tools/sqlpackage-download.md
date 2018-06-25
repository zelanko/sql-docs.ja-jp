---
title: ダウンロードしてインストール sqlpackage |Microsoft ドキュメント
description: ダウンロードして、Windows、macOS、または Linux 用 sqlpackage をインストール
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 4e5528ca046de83385171890fbda389928e41cf3
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703841"
---
# <a name="download-and-install-sqlpackage"></a>ダウンロードしてインストール sqlpackage

sqlpackage は、Windows、macOS、および Linux で実行されます。

ダウンロードして、最新の .NET Framework リリースおよび macOS と Linux のプレビューをインストールします。

|プラットフォーム|ダウンロード|リリース日|[バージョンのオプション]|ビルド|
|:---|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=875508)|2018 年 1 月 25日|17.4.1|14.0.3917.1|
|macOS (プレビュー)|[.zip](https://go.microsoft.com/fwlink/?linkid=873927)|2018 年 5 月 9 日 |0.0.1|15.0.4057.1|
|Linux (プレビュー)|[.zip](https://go.microsoft.com/fwlink/?linkid=873926)|2018 年 5 月 9 日 |0.0.1|15.0.4057.1|

## <a name="get-sqlpackage-for-windows"></a>Windows の sqlpackage を取得します。

Sqlpackage の今回のリリースには、標準的な Windows インストーラーのエクスペリエンスと .zip が含まれます。 

**インストーラー**

1. ダウンロードし、実行、 [DacFramework.msi Windows 用のインストーラー](https://go.microsoft.com/fwlink/?linkid=875508)です。
2. 新しいコマンド プロンプト ウィンドウを開き、sqlpackage.exe を実行します。
    - sqlpackage にインストールされている、```C:\Program Files\Microsoft SQL Server\140\DAC\bin```フォルダー

## <a name="get-sqlpackage-preview-for-macos"></a>MacOS の sqlpackage (プレビュー) を取得します。

1. ダウンロード[macOS の sqlpackage](https://go.microsoft.com/fwlink/?linkid=873927)です。
2. ファイルを抽出して sqlpackage を起動して、新しいターミナル ウィンドウを開き、次のコマンドを入力します。

   **.zip のインストール:**
   ```bash 
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage 
   ``` 

## <a name="get-sqlpackage-preview-for-linux"></a>Linux 用 sqlpackage (プレビュー) を取得します。

1. ダウンロード[for Linux sqlpackage](https://go.microsoft.com/fwlink/?linkid=873926)インストーラーまたは tar.gz アーカイブのいずれかを使用します。
2. ファイルを抽出して sqlpackage を起動して、新しいターミナル ウィンドウを開き、次のコマンドを入力します。

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
   > Debian、red Hat、および Ubuntu で見つからない依存関係があります。 Linux のバージョンに応じてこれらの依存関係をインストールするのにには、次のコマンドを使用します。
   

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


## <a name="uninstall-sqlpackage-preview"></a>Sqlpackage (プレビュー) アンインストールします。

Windows インストーラーを使用して sqlpackage をインストールした場合は、すべての Windows アプリケーションを削除すると同じ方法をアンインストールしてください。

.Zip やその他のアーカイブと共に sqlpackage をインストールする場合は、ファイルを削除し、単にします。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

sqlpackage は、Windows、macOS など、Linux で実行されは、次のプラットフォームでサポートされています。

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
- macOS 10.13 高 Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- 詳細については[sqlpackage](sqlpackage.md)

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
