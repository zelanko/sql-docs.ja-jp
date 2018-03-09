---
title: "ダウンロードし、インストールの Microsoft SQL 操作 Studio (プレビュー) |Microsoft ドキュメント"
description: "ダウンロードおよびインストール Microsoft SQL 操作 (プレビュー) 対応の Studio Windows、macOS、または Linux"
ms.custom: tools|sos
ms.date: 03/05/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1cb41e1824fc157932e2cb08292608bb97e46712
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>ダウンロードして SQL 操作 Studio (プレビュー) のインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で実行されます。

ダウンロードし、最新のリリースをインストール、*年 2 月のパブリック プレビュー*:

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=867998)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=867997)|2018 年 2 月 15日 |0.26.7|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=867999)|2018 年 2 月 15日 |0.26.7|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=868002)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=868001)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=868000)|2018 年 2 月 15日|0.26.7|

最新のリリースに関する詳細については、次を参照してください。、[リリース ノート](release-notes.md)です。

## <a name="get-sql-operations-studio-preview-for-windows"></a>Windows 用の SQL 操作 Studio (プレビュー) の取得します。

このリリースの[!INCLUDE[name-sos](../includes/name-sos-short.md)]標準的な Windows インストーラーのエクスペリエンスと .zip が含まれます。 

**インストーラー**

1. ダウンロードし、実行、 [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] Windows 用のインストーラー](https://go.microsoft.com/fwlink/?linkid=867998)です。
1. 開始、[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]アプリ。


**.zip file**

1. ダウンロード[ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for Windows .zip](https://go.microsoft.com/fwlink/?linkid=867997)です。
2. ダウンロードしたファイルを参照し、抽出しています。
3. 実行します。 `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>MacOS の SQL 操作 Studio (プレビュー) を取得します。

1. ダウンロード[ [!INCLUDE[name-sos](../includes/name-sos-short.md)] macOS の](https://go.microsoft.com/fwlink/?linkid=867999)します。
2. Zip の内容を展開しをダブルクリックします。
3. させる[!INCLUDE[name-sos](../includes/name-sos-short.md)]で使用できる、*スタート パッド*、ドラッグ*sqlops.app*を*アプリケーション*フォルダーです。


## <a name="get-sql-operations-studio-preview-for-linux"></a>Linux 用の SQL 操作 Studio (プレビュー) の取得します。

1. ダウンロード[ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for Linux](https://go.microsoft.com/fwlink/?linkid=868000)です。
1. ファイルと起動を抽出する[!INCLUDE[name-sos](../includes/name-sos-short.md)]新しいターミナル ウィンドウを開きを次のコマンドを入力します。

   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   > [!NOTE]
   > Debian、red Hat、および Ubuntu で見つからない依存関係があります。 Linux のバージョンに応じてこれらの依存関係をインストールするのにには、次のコマンドを使用します。
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>SQL 操作 Studio (プレビュー) アンインストールします。

インストールした場合[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]すべての Windows アプリケーションを削除するのと同じ方法をアンインストールし、Windows インストーラーを使用します。

インストールした場合[!INCLUDE[name-sos-short](../includes/name-sos-short.md)].zip やその他のアーカイブは、単にファイルを削除します。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Windows、macOS など、Linux で実行され、次のプラットフォームではサポートされています。

### <a name="windows"></a>Windows
- Windows 10 (64 ビット)
- Windows 8.1 (64 ビット)
- Windows 8 (64 ビット)
- Windows 7 (SP1) (64 ビット) - 必要があります[KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

### <a name="macos"></a>macOS
- macOS 10.13 高 Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>更新を確認する
最新の更新プログラムを確認するに をクリックし、ウィンドウの左下の歯車アイコンをクリックして**更新プログラムの確認**

## <a name="next-steps"></a>次の手順

作業を開始する次のクイック スタートのいずれかを参照してください。
- [接続し、クエリの SQL Server](quickstart-sql-server.md)
- [接続し、Azure SQL データベースの照会](quickstart-sql-database.md)
- [接続し、Azure データ ウェアハウスのクエリ](quickstart-sql-dw.md)

投稿[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)です。
