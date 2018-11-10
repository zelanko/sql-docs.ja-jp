---
title: ダウンロードし、Azure Data Studio のインストール |Microsoft Docs
description: ダウンロードと Windows 用の Azure データ Studio のインストール、macOS、または Linux
ms.custom: tools|sos
ms.date: 11/06/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f177b7756a1afc7d28f4f3bd85ac46c1f7563cbe
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217810"
---
# <a name="download-and-install-azure-data-studio"></a>ダウンロードし、Azure Data Studio のインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で動作します。

ダウンロードして、最新のリリースでは、インストール、*年 11 月リリース*:

> [!NOTE]
> SQL Operations Studio から更新しているし、設定、キーボード ショートカット、またはコード スニペットを保持する場合は、次を参照してください。[ユーザー設定の移動](#move-user-settings)します。

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=2038320)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2038323)|2018 年 11 月 6 日 |1.2.4|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2038327)|2018 年 11 月 6 日 |1.2.4|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2038405)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2038401)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2038332)|2018 年 11 月 6 日 |1.2.4|

最新のリリースに関する詳細は、次の [リリース ノート](release-notes.md) を参照してください。

## <a name="get-azure-data-studio-for-windows"></a>Windows 用 Azure Data Studio を入手します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)]のこのリリースは標準的な Windows インストーラーと .zip を含んでいます。 

**インストーラー**

1. [Windows 用の [!INCLUDE[name-sos](../includes/name-sos-short.md)] インストーラー](https://go.microsoft.com/fwlink/?linkid=2038320) ダウンロードして実行します。
1. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]のアプリを開始します。


**zip ファイル**

1. [[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Windows .zip](https://go.microsoft.com/fwlink/?linkid=2038323) をダウンロードします。
2. ダウンロードしたファイルを参照し、展開します。
3. `\azuredatastudio-windows\azuredatastudio.exe`を実行します。


## <a name="get-azure-data-studio-for-macos"></a>MacOS 用の Azure データ Studio を入手します。

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for macOS](https://go.microsoft.com/fwlink/?linkid=2038327) をダウンロードします。
2. zip のコンテンツを展開するには、ダブルクリックします。
3. させる[!INCLUDE[name-sos](../includes/name-sos-short.md)]で使用できる、*スタート パッド*、ドラッグ*Azure データ Studio.app*を*アプリケーション*フォルダー。


## <a name="get-azure-data-studio-for-linux"></a>Linux 用 Azure Data Studio を入手します。

1. ダウンロード[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Linux を使用して、インストーラーまたは tar.gz アーカイブのいずれかで。
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2038405)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2038401)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2038332)
1. ファイルを展開し、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を起動するため、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   **Debian のインストール:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **rpm のインストール:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **tar.gz インストール:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Debian、Redhat、および Ubuntu で、依存関係が見つからないことがあります。 これらの依存関係をインストールするために、Linux のバージョンに応じて、次のコマンドを使用してください。
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
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


## <a name="uninstall-azure-data-studio"></a>Azure Data Studio をアンインストールします。

Windows インストーラーを使用して[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]をインストールした場合、他の Windows アプリケーションの削除と同じ方法でアンインストールしてください。

.zip またはその他のアーカイブから [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] をインストールした場合、ファイルを削除してください。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

[!INCLUDE[name-sos](../includes/name-sos-short.md)] は Windows、macOS、そして Linux で動作し、次のプラットフォームでサポートされています。

### <a name="windows"></a>Windows
- Windows 10 (64 ビット)
- Windows 8.1 (64 ビット)
- Windows 8 (64 ビット)
- Windows 7 (SP1) (64 ビット) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767) が必要です
- Windows Server 2016
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>推奨システム要件
最適なエクスペリエンスは、推奨システム要件を使用してください。

|             | CPU コア | メモリと RAM |
|:-----------:|:---------:|:----------:|
| 推奨 |     4     |      8     |
|   最小   |     2     |      4     |
|             |           |            |

## <a name="check-for-updates"></a>更新を確認する
最新の更新を確認するには、ウィンドウの左下にある歯車アイコンをクリックして **更新を確認する** をクリックしてください。

## <a name="supported-sql-offerings"></a>サポートされる SQL 製品

* このバージョンの Azure データ Studio はすべて[サポート対象バージョンの SQL Server 2014 - [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) Azure SQL Database と Azure SQL Data Warehouse で最新のクラウド機能の使用をサポートしています。 Azure Data Studio には、Azure SQL マネージ インスタンスのプレビュー サポートも提供します。

## <a name="move-user-settings"></a>ユーザー設定を移動します。

カスタム設定を移動する場合はキーボード ショートカット、またはコード スニペットでは、以下の手順に従います。 これは、SQL Operations Studio のバージョンから Azure Data Studio にアップグレードする場合に重要です。

*Azure Data Studio が既にあるか、インストールまたは SQL Operations Studio をカスタマイズしたことはありません、このセクションを無視できます。*


1. 左下にある歯車をクリックして設定を開く**設定します。**

   ![オープン設定](./media/download/open-settings.png)

2. 右クリックし、**ユーザー設定**上部タブし、をクリックして**エクスプ ローラーで表示**

   ![エクスプ ローラーの表示](./media/download/reveal-in-explorer.png)

3. このフォルダー内のすべてのファイルをコピーし、ドキュメント フォルダーのように、ローカル ドライブ上の場所を検索する形で保存します。

   ![設定のコピー](./media/download/copy-settings.png)

4. 新しいバージョンの Azure Data Studio、手順 3 の後は、1 ~ 2 がフォルダーに保存した内容を貼り付ける手順に従います。 設定、キー バインド、またはスニペットではそれぞれの場所を手動でコピーできます。

5. 既存のインストールを上書きする場合は、リソース エクスプ ローラーの Azure アカウントへの接続エラーを回避するためにインストールする前に、古いインストール ディレクトリを削除します。

## <a name="next-steps"></a>次の手順

開始する次のクイック スタートのいずれかを参照してください。
- [接続および SQL Server のクエリ](quickstart-sql-server.md)
- [接続および Azure SQL Database のクエリ](quickstart-sql-database.md)
- [接続し、Azure Data Warehouse に対するクエリ](quickstart-sql-dw.md)

投稿する[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)します。
