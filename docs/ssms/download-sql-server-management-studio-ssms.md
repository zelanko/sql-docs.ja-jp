---
title: SQL Server Management Studio (SSMS) のダウンロード | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
ms.technology: ssms
ms.topic: conceptual
keywords:
- ssms のインストール、ssms のダウンロード、最新の ssms
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- sql management studio インストール
- ダウンロード sql management studio
- ms sql management studio
- install sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
author: dnethi
ms.author: dinethi
manager: craigg
ms.openlocfilehash: 4e109a44ced3a640ee64f7099dc45da5655c5e3f
ms.sourcegitcommit: 670082cb47f7d3d82e987b549b6f8e3a8968b5db
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57334729"
---
# <a name="download-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) のダウンロード
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server Management Studio (SSMS) は、SQL Server から Azure SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS には、SQL Server とデータベースのインスタンスを構成、監視、および管理するためのツールが備わっています。 SSMS を使用して、アプリケーションで使われるデータ層コンポーネントを配置、監視、アップグレードしたり、クエリとスクリプトを作成したりすることもできます。

SSMS を使用すると、データベースとデータ ウェアハウスがローカル コンピューターやクラウドなど、どこにあっても、クエリ、設計、および管理ができます。

SSMS は無料です。

[SSMS 18.0 パブリック プレビュー 7 をご利用いただけるようになりました](#ssms-180-preview-7)。これは *SQL Server Management Studio* の最新世代であり、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] をサポートしています。

## <a name="ssms-1791-is-the-current-general-availability-ga-version-of-ssms"></a>SSMS 17.9.1 は現在 SSMS の一般公開 (GA) バージョンである

[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 17.9.1 のダウンロード](https://go.microsoft.com/fwlink/?linkid=2043154)

[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 17.9.1 アップグレード パッケージのダウンロード (17.x から 17.9.1 へのアップグレード)](https://go.microsoft.com/fwlink/?linkid=2043430)

**バージョン情報**

- リリース番号:17.9.1<br>
- ビルド番号:14.0.17289.0<br>
- リリース日:2018 年 11 月 21 日

### <a name="available-languages-ssms-1791"></a>使用できる言語 (SSMS 17.9.1)

> [!NOTE]
> SSMS 17.x の英語以外のローカライズされたリリースでは、次のものにインストールする場合、[KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/kb/2862966)が必要です:Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2。

[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

SSMS 17.9.1 について詳しくは、[SSMS 17.9.1 の変更ログ](sql-server-management-studio-changelog-ssms.md#ssms-1791-latest-ga-release)に関するページをご覧ください。

## <a name="ssms-installation-tips-and-issues-ssms-1791"></a>SSMS のインストールに関するヒントと問題 (SSMS 17.9.1)

### <a name="minimize-installation-reboots"></a>インストール時の再起動を最小限に抑える

* SSMS のセットアップでインストールの最後に再起動が必要になる可能性を低くするには、次の操作を実行します。
  * 最新バージョンの Visual C++ 2013 再頒布可能パッケージを実行します。 バージョン 12.0.40649.5 (またはそれ以降) が必要です。 必要なのは x64 バージョンのみです。
  * コンピューターの .NET Framework のバージョンが 4.6.1 (またはそれ以降) であることを確認します。
  * コンピューターで開かれている Visual Studio のすべてのインスタンスを閉じます。
  * OS の最新の更新プログラムがすべてコンピューターにインストールされていることを確認します。
  * これらの操作は通常、1 回だけ必要です。 SSMS の同じメジャー バージョンに対する追加アップグレードの間に、再起動が必要になる場合があります。 マイナー アップグレードでは、SSMS のすべての前提条件は既にコンピューターにインストールされています。

## <a name="ssms-180-preview-7"></a>SSMS 18.0 (プレビュー 7)

**SSMS 18.0 パブリック プレビュー 7 をご利用いただけるようになりました。これは *SQL Server Management Studio* の最新世代であり、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] をサポートしています。**

**[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 18.0 (プレビュー 7) のダウンロード](https://go.microsoft.com/fwlink/?linkid=2078638)**

*プレビュー 7* は、SSMS 18.0 の最新のパブリック プレビューです。 以前の SSMS 18.0 プレビューがインストールされている場合は、それをアンインストールしてから SSMS 18.0 プレビュー 7 をインストールします。

**バージョン情報**

- リリース番号:18.0 (プレビュー 7)<br>
- ビルド番号:15.0.18092.0<br>
- リリース日:2019 年 3 月 1 日

コメントや提案がある場合、または問題を報告する場合、SSMS チームに連絡する最適な方法は [UserVoice](https://aka.ms/sqlfeedback) です。

SSMS 18.x のインストールでは、17.x 以前のバージョンの SSMS がアップグレードまたは置き換えられることはありません。 SSMS 18.x は以前のバージョンとは別にサイド バイ サイドでインストールされるので、両方のバージョンを使用できます。

コンピューターに SSMS のサイド バイ サイドのインストールが含まれている場合は、特定のニーズに応じて適切なバージョンを起動してください。 最新バージョンには、**Microsoft SQL Server Management Studio 18** というラベルが付いています。
 
## <a name="available-languages-ssms-180-preview-7"></a>使用可能な言語 (SSMS 18.0 プレビュー 7)

SSMS の今回のリリースは、次の言語でインストールできます。

SQL Server Management Studio 18.0 (プレビュー 7):<br>
[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2078638&clcid=0x40a)

SQL Server Management Studio 18.0 アップグレード パッケージ (18.0 へのアップグレード):<br>
現在、利用できるアップグレード オプションはありません。 以前の SSMS 18.0 プレビューがインストールされている場合は、それをアンインストールしてから SSMS 18.0 プレビュー 7 をインストールします。

> [!NOTE]
> SQL Server PowerShell モジュールは、PowerShell ギャラリーで入手できる独立したインストールです。 詳細については、「[SQL Server PowerShell モジュールのダウンロード](download-sql-server-ps-module.md)」を参照してください。

## <a name="new-in-this-release-ssms-180-preview-7"></a>このリリースでの新機能 (SSMS 18.0 プレビュー 7)

SSMS 18.0 (プレビュー 7) は SQL Server Management Studio の最新バージョンです。 SSMS の 18.x 世代は、SQL Server 2008 から SQL Server 2019 プレビューまでのほぼすべての機能領域をサポートしています。

このリリースの新機能について詳しくは、[SSMS の変更ログ](sql-server-management-studio-changelog-ssms.md)に関するページをご覧ください。

## <a name="supported-sql-offerings-ssms-180-preview-7"></a>サポートされる SQL 製品 (SSMS 18.0 プレビュー 7)

* このバージョンの SSMS は、すべての[サポート対象バージョンである SQL Server 2008 から [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) で動作し、Azure SQL Database および Azure SQL Data Warehouse で最新のクラウド機能と連携するための最大レベルのサポートを提供します。
* また、SSMS 18.x は、SSMS 17.x、SSMS 16.x または SQL Server 2014 SSMS 以前とサイドバイサイドでインストールできます。
* SQL Server Integration Services (SSIS) - SSMS バージョン 17.x 以降では、レガシ SQL Server Integration Services サービスへの接続はサポートされません。 以前のバージョンのレガシ Integration Services に接続するには、SQL Server のバージョンに対応する SSMS のバージョンを使用します。 たとえば、レガシ SQL Server 2016 Integration Services サービスに接続する場合は、SSMS 16.x を使用します。 SSMS 17.x および SSMS 16.x は同じコンピューターにサイド バイ サイドでインストールすることができます。 SQL Server 2012 のリリース以降では、SSIS カタログ データベースである SSISDB を使用して、Integration Services パッケージの格納、管理、実行、監視を行うことをお勧めします。 詳細については、「[SSIS カタログ](../integration-services/catalog/ssis-catalog.md)」をご覧ください。

## <a name="supported-operating-systems-ssms-180-preview-7"></a>サポートされるオペレーティング システム (SSMS 18.0 プレビュー 7)

SSMS の今回のリリースでは、最新の Service Pack を使用した次の 64 ビット プラットフォームがサポートされます。

- Windows 10 (64 ビット) <sup>*</sup>
- Windows Server 2016 <sup>*</sup>
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

<sup>*</sup> バージョン 1607 (10.0.14939) 以降が必要

> [!NOTE]
> SSMS は Windows 上でのみ実行されます。 Windows 以外のプラットフォーム上で実行されるツールが必要な場合は、Azure Data Studio をご覧ください。 Azure Data Studio は、macOS、Linux、さらに Windows 上で実行される新しいクロスプラットフォーム ツールです。 詳しくは、[Azure Data Studio](../azure-data-studio/what-is.md) に関する記事をご覧ください。
  
## <a name="release-notes-ssms-180-preview-7"></a>リリース ノート(SSMS 18.0 プレビュー 7)

なし

## <a name="previous-releases"></a>以前のリリース

[SQL Server Management Studio の以前のリリース](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>フィードバック

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL クライアント ツール フォーラム](https://social.msdn.microsoft.com/Forums/home?forum=sqltools)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a>参照

- [チュートリアル:SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [SQL Server Management Studio のドキュメント](sql-server-management-studio-ssms.md)
- [追加の更新プログラムとサービス パック](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

コメントや提案がある場合、または問題を報告する場合、SSMS チームに連絡する最適な方法は [UserVoice](https://aka.ms/sqlfeedback) です。
