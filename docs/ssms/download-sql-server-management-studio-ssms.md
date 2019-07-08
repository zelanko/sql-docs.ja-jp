---
title: SQL Server Management Studio (SSMS) のダウンロード | Microsoft Docs
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
ms.custom: ''
ms.date: 06/12/2019
ms.openlocfilehash: 403ca9e5132a00f003aa67a2011d98d0044b4807
ms.sourcegitcommit: 65ceea905030582f8d89e75e97758abf3b1f0bd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67399659"
---
# <a name="download-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) のダウンロード

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server Management Studio (SSMS) は、SQL Server から Azure SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS には、SQL Server とデータベースのインスタンスを構成、監視、および管理するためのツールが備わっています。 SSMS を使用して、アプリケーションで使われるデータ層コンポーネントを配置、監視、アップグレードしたり、クエリとスクリプトを作成したりすることもできます。

SSMS を使用すると、データベースとデータ ウェアハウスがローカル コンピューターやクラウドなど、どこにあっても、クエリ、設計、および管理ができます。

SSMS は無料です。

## <a name="download-ssms-181"></a>SSMS 18.1 のダウンロード

**SSMS 18.1 をご利用いただけるようになりました。これは *SQL Server Management Studio* の GA (一般提供) 最新版であり、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]!** に対応しています。

**[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 18.1 のダウンロード ](https://go.microsoft.com/fwlink/?linkid=2094583)**

SSMS 18.1 は SSMS の GA (一般提供) 最新版です。 SSMS 18.0 (GA) をインストールしている場合、SSMS 18.1 をインストールすると、18.1 にアップグレードされます。 以前の*プレビュー*版の SSMS 18.0 がインストールされている場合は、それをアンインストールしてから SSMS 18.1 をインストールしてください。

**バージョン情報**

- リリース番号:18.1<br>
- ビルド番号:15.0.18131.0<br>
- リリース日:2019 年 6 月 11 日

コメントや提案がある場合、または問題を報告する場合、SSMS チームに連絡する最適な方法は [UserVoice](https://aka.ms/sqlfeedback) です。

SSMS 18.x のインストールでは、17.x 以前のバージョンの SSMS がアップグレードまたは置き換えられることはありません。 SSMS 18.x は以前のバージョンとは別にサイド バイ サイドでインストールされるので、両方のバージョンを使用できます。

コンピューターに SSMS のサイド バイ サイドのインストールが含まれている場合は、特定のニーズに応じて適切なバージョンを起動してください。 最新バージョンには、**Microsoft SQL Server Management Studio 18** というラベルが付いています。

## <a name="available-languages-ssms-181"></a>使用できる言語 (SSMS 18.1)

SSMS の今回のリリースは、次の言語でインストールできます。

SQL Server Management Studio 18.1:<br>
[中国語 (簡体字)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x804) | [中国語 (繁体字)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40a)

> [!NOTE]
> SQL Server PowerShell モジュールは、PowerShell ギャラリーで入手できる独立したインストールです。 詳細については、「[SQL Server PowerShell モジュールのダウンロード](download-sql-server-ps-module.md)」を参照してください。

## <a name="new-in-this-release-ssms-181"></a>このリリースの新機能 (SSMS 18.1)

- **データベース ダイアグラム** - データベース ダイアグラムが SSMS に戻りました。 詳細については、「[データベース ダイアグラム](https://feedback.azure.com/forums/908035/suggestions/37507828)」を参照してください。
- **SSBDIAGNOSE.EXE** - SQL Server Diagnose コマンド ライン ツールが SSMS パッケージに戻りました。
- **Integration Services (SSIS)** - Azure で、Azure またはファイル システムの SSIS カタログにある SSIS パッケージのスケジュールをサポート。 [新しいスケジュール] ダイアログを起動するためのエントリが 3 つあります。Azure の SSIS カタログにある SSIS パッケージを右クリックしたときに表示される *[新しいスケジュール]* メニュー項目、 *[ツール]* メニューの *[Azure への移行]* メニュー項目にある *[Schedule SSIS Package in Azure]\(\Azure で SSIS パッケージをスケジュールする)* メニュー項目、Azure SQL Database Managed Instance の下で [ジョブ] フォルダーを右クリックしたときに表示される [Schedule SSIS in Azure]\(Azure で SSIS をスケジュールする\) です。

このリリースの新機能の詳細については、[SSMS のリリース ノート](release-notes-ssms.md)に関するページをご覧ください。

## <a name="supported-sql-offerings-ssms-181"></a>サポートされる SQL 製品 (SSMS 18.1)

* このバージョンの SSMS は、すべての[サポート対象バージョンである SQL Server 2008 から [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) で動作し、Azure SQL Database および Azure SQL Data Warehouse で最新のクラウド機能と連携するための最大レベルのサポートを提供します。
* また、SSMS 18.x は、SSMS 17.x、SSMS 16.x または SQL Server 2014 SSMS 以前とサイドバイサイドでインストールできます。
* SQL Server Integration Services (SSIS) - SSMS バージョン 17.x 以降では、レガシ SQL Server Integration Services サービスへの接続はサポートされません。 以前のバージョンのレガシ Integration Services に接続するには、SQL Server のバージョンに対応する SSMS のバージョンを使用します。 たとえば、レガシ SQL Server 2016 Integration Services サービスに接続する場合は、SSMS 16.x を使用します。 SSMS 17.x および SSMS 16.x は同じコンピューターにサイド バイ サイドでインストールすることができます。 SQL Server 2012 のリリース以降では、SSIS カタログ データベースである SSISDB を使用して、Integration Services パッケージの格納、管理、実行、監視を行うことをお勧めします。 詳細については、「[SSIS カタログ](../integration-services/catalog/ssis-catalog.md)」をご覧ください。

## <a name="supported-operating-systems-ssms-181"></a>サポートされるオペレーティング システム (SSMS 18.1)

SSMS の今回のリリースでは、最新の Service Pack を使用した次の 64 ビット プラットフォームがサポートされます。

- Windows 10 (64 ビット) <sup>*</sup>
- Windows 8.1 (64 ビット)
- Windows Server 2019 (64 ビット)
- Windows Server 2016 (64 ビット) <sup>*</sup>
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

<sup>*</sup> バージョン 1607 (10.0.14393) 以降が必要

> [!NOTE]
> SSMS は Windows 上でのみ実行されます。 Windows 以外のプラットフォーム上で実行されるツールが必要な場合は、Azure Data Studio をご覧ください。 Azure Data Studio は、macOS、Linux、さらに Windows 上で実行される新しいクロスプラットフォーム ツールです。 詳しくは、[Azure Data Studio](../azure-data-studio/what-is.md) に関する記事をご覧ください。

## <a name="release-notes-ssms-181"></a>リリース ノート (SSMS 18.1)

このリリースには、[既知の問題](release-notes-ssms.md#known-issues-181)がいくつかあります。

このリリースの詳細については、[SSMS のリリース ノート](release-notes-ssms.md)に関するページをご覧ください。

## <a name="previous-ssms-releases"></a>以前のリリースの SSMS

[SQL Server Management Studio の以前のリリース](../ssms/release-notes-ssms.md#previous-ssms-releases)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>参照

- [チュートリアル:SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [SQL Server Management Studio のドキュメント](sql-server-management-studio-ssms.md)
- [追加の更新プログラムとサービス パック](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
