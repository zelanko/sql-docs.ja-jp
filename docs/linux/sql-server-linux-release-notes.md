---
title: Linux 上の SQL Server 2017 のリリースノート
description: この記事には、Linux で実行されている SQL Server 2017 のリリースノートとサポートされる機能が含まれています。 リリースノートは、最新のリリースと以前のいくつかのリリースに含まれています。
author: VanMSFT
ms.author: vanto
ms.date: 06/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 5b6fce0bdde7e320eea0371125a61627652de80d
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388414"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 のリリースノート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次のリリースノートは、 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] Linux でのの実行に適用されます。 この記事は、各リリースのセクションに分けられています。 GA リリースには、詳細なサポートと既知の問題が記載されています。 各累積的な更新プログラム (CU) または一般配布リリース (GDR) には、CU の変更について説明するサポート記事へのリンクと、Linux パッケージのダウンロードへのリンクがあります。

> [!TIP]
> これらのリリースノートは、 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]特にリリースを対象としています。 新しい[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]の詳細については、「 [Linux での SQL Server 2019 preview のリリースノート](sql-server-linux-release-notes-2019.md?view=sql-server-ver15)」を参照してください。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3、7.4、7.5、または7.6 サーバー | XFS または EXT4 | [インストールガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS または EXT4 | [インストールガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS または EXT4 | [インストールガイド](quickstart-install-connect-ubuntu.md) | 
| Windows、Mac、または Linux での Docker エンジン1.8 以降 | なし | [インストールガイド](quickstart-install-connect-docker.md) | 

> [!TIP]
> 詳細については、Linux 上の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の[システム要件](sql-server-linux-setup.md#system)を確認してください。 の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]最新のサポートポリシーについては、 [Microsoft SQL Server のテクニカルサポートポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)を参照してください。

## <a name="tools"></a>ツール

を対象[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]とする既存のクライアントツールの[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]多くは、Linux での実行をシームレスにターゲットにすることができます。 一部のツールには、Linux で適切に動作するために特定のバージョンの要件がある場合があります。 ツールの[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]完全な一覧については、「 [SQL Server 用の SQL ツールとユーティリティ](../tools/overview-sql-tools.md)」を参照してください。

## <a name="release-history"></a>リリース履歴

次の表に、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]リリース履歴を示します。

| リリース               | バージョン       | リリース日 |
|-----------------------|---------------|--------------|
| [CU15](#CU15)         | 14.0.3162.1   | 2019-05-23   |
| [CU14](#CU14)         | 14.0.3076.1   | 2019-03-25   |
| [CU13](#CU13)         | 14.0.3048.4   | 2018-12-18   |
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [GA](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a>更新プログラムのインストール方法

Cu リポジトリ (**mssql-server-2017**) を構成している場合は、新規インストールを実行すると[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、最新の cu パッケージが取得されます。 CU リポジトリは、Linux 上ののすべての[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]パッケージインストール記事の既定値です。 GDR リポジトリ (**mssql-server-2017-GDR**) を構成している場合は、GA 以降にリリースされた重要なセキュリティ更新プログラムのみが取得されます。 Docker コンテナー CU または GDR 更新プログラムが必要な場合は、 [Docker エンジン用の Microsoft SQL Server on Linux](https://hub.docker.com/r/microsoft/mssql-server)の公式イメージを参照してください。 リポジトリの構成の詳細については、「 [Configure repository for SQL Server on Linux](sql-server-linux-change-repo.md)」を参照してください。

既存[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のパッケージを更新する場合は、パッケージごとに適切な更新コマンドを実行して、最新の CU を取得します。 各パッケージの特定の更新手順については、次のインストールガイドを参照してください。

- [SQL Server パッケージのインストール](sql-server-linux-setup.md#upgrade)
- [フルテキスト検索パッケージのインストール](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)
- [SQL Server エージェントを有効にする](sql-server-linux-setup-sql-agent.md)

## <a id="CU15"></a>CU15 (2019 年5月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 15 (CU15) リリースです。 このリリースのバージョンは14.0.3162.1 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/en-us/help/4498951](https://support.microsoft.com/en-us/help/4498951)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3162.1-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3162.1-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3162.1-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3162.1-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3162.1-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3162.1-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU14"></a>CU14 (3 月 2019)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 14 (CU14) リリースです。 このリリースのバージョンは14.0.3076.1 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4484710](https://support.microsoft.com/help/4484710)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3076.1-2 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3076.1-2 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3076.1-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a>CU13 (2018 年12月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 13 (CU13) リリースです。 このリリースのバージョンは14.0.3048.4 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4466404](https://support.microsoft.com/help/4466404)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3048.4-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3048.4-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3048.4-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a>CU12 (10 月 2018)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 12 (CU12) リリースです。 このリリースのバージョンは14.0.3045.24 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4464082](https://support.microsoft.com/help/4464082)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3045.24-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3045.24-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3045.24-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a>CU11 (9 月 2018)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 11 (CU11) リリースです。 このリリースのバージョンは14.0.3038.14 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4462262](https://support.microsoft.com/help/4462262)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3038.14-2 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3038.14-2 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3038.14-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a>CU10 (2018 年8月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 10 (CU10) リリースです。 このリリースのバージョンは14.0.3037.1 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4342123](https://support.microsoft.com/help/4342123)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3037.1-2 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3037.1-2 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3037.1-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a>CU9-GDR2 (2018 年8月)

これは、用に[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]以前にリリースされた CU (CU9) も含まれるセキュリティ更新プログラムです。 このリリースのバージョンは14.0.3035.2 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4293805](https://support.microsoft.com/help/4293805)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3035.2-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| SLES RPM パッケージ | 14.0.3035.2-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3035.2-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a>GDR2 (2018 年8月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]GDR2 (および GDR1) セキュリティ修正プログラムのみが含まれるセキュリティ更新プログラムです。  このリリースのバージョンは14.0.2002.14 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4293803](https://support.microsoft.com/help/4293803)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.2002.14-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.2002.14-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.2002.14-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a>CU9 (2018 年7月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 9 (CU9) リリースです。 このリリースのバージョンは14.0.3030.27 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4341265](https://support.microsoft.com/help/4341265)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3030.27-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3030.27-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3030.27-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a>CU8 (2018 年6月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 8 (CU8) リリースです。 このリリースのバージョンは14.0.3029.16 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4338363](https://support.microsoft.com/help/4338363)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3029.16-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3029.16-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3029.16-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a>CU7 (2018 年5月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 7 (CU7) リリースです。 このリリースのバージョンは14.0.3026.27 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4229789](https://support.microsoft.com/help/4229789)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3026.27-2 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3026.27-2 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3026.27-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a>CU6 (Apr 2018)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 6 (CU6) リリースです。 このリリースのバージョンは14.0.3025.34 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3025.34-3 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3025.34-3 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3025.34-3 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a>CU5 (3 月 2018)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 5 (CU5) リリースです。 このリリースのバージョンは14.0.3023.8 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4092643](https://support.microsoft.com/help/4092643)ては、「」を参照してください。

### <a name="known-upgrade-issue"></a>アップグレードに関する既知の問題

以前のリリースから CU5 にアップグレードすると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]次のエラーが発生してを起動できないことがあります。

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

このエラーを解決するには、SQL Server エージェント[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を有効にし、次のコマンドを使用して再起動します。

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3023.8-5 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3023.8-5 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3023.8-5 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a>CU4 (2018 年2月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 4 (CU4) リリースです。 このリリースのバージョンは14.0.3022.28 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4056498](https://support.microsoft.com/help/4056498)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

> [!NOTE]
> CU4 の時点では、SQL Server エージェントは別のパッケージとしてインストールされなくなりました。 エンジンパッケージと共にインストールされ、を使用できるようにする必要があります。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3022.28-2 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3022.28-2 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3022.28-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a>GDR1 (Jan 2018)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]GDR1 セキュリティ修正プログラムのみが含まれるセキュリティ更新プログラムです。 このリリースのバージョンは14.0.2000.63 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4057122](https://support.microsoft.com/help/4057122)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.2000.63-3 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.2000.63-3 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.2000.63-3 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a>CU3 (Jan 2018)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 3 (CU3) リリースです。 このリリースのバージョンは14.0.3015.40 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4052987](https://support.microsoft.com/help/4052987)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3015.40-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3015.40-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3015.40-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[SQL Server エージェント Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a>CU2 (2017 年11月)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 2 (CU2) リリースです。 このリリースのバージョンは14.0.3008.27 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3008.27-1 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3008.27-1 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3008.27-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[SQL Server エージェント Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a>CU1 (10 月 2017)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]累積的な更新プログラム 1 (CU1) リリースです。 このリリースのバージョンは14.0.3006.16 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] このリリースの修正プログラムと機能強化の詳細につい[https://support.microsoft.com/help/KB4053439](https://support.microsoft.com/help/4038634)ては、「」を参照してください。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージインストールの場合は、次の表の情報を使用して RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3006.16-3 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3006.16-3 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3006.16-3 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[SQL Server エージェント Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a>GA (10 月 2017)

これは、の[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]一般公開 (GA) リリースです。 このリリースのバージョンは14.0.1000.169 です。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]

### <a name="package-details"></a>パッケージの詳細

次の表に、RPM と Debian パッケージのパッケージの詳細とダウンロード場所を示します。 次のインストールガイドの手順を使用する場合は、これらのパッケージを直接ダウンロードする必要はありません。

- [SQL Server パッケージのインストール](sql-server-linux-setup.md)
- [フルテキスト検索パッケージのインストール](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェントパッケージのインストール](sql-server-linux-setup-sql-agent.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.1000.169-2 | [エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.1000.169-2 | [mssql-サーバーエンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[フルテキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.1000.169-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[SQL Server エージェント Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a>サポートされていない機能 & サービス

GA リリース時の Linux では、次の機能とサービスは使用できません。 これらの機能のサポートは、時間の経過と共に増加します。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | トランザクション レプリケーション |
| &nbsp; | マージ レプリケーション |
| &nbsp; | 変更データキャプチャ (「SQL Server エージェント」を参照) |
| &nbsp; | Stretch DB |
| &nbsp; | PolyBase |
| &nbsp; | サードパーティ接続を使用した分散クエリ |
| &nbsp; | 以外のデータソースへのリンクサーバー[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | システム拡張ストアドプロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable、FILESTREAM |
| &nbsp; | EXTERNAL_ACCESS または UNSAFE 権限セットを持つ CLR アセンブリ |
| &nbsp; | バッファー プール拡張 |
| **SQL Server エージェント** |  システムCmdExec、PowerShell、キューリーダー、SSIS、SSAS、SSRS |
| &nbsp; | オブジェクト エクスプローラーには |
| &nbsp; | ログ リーダー エージェント (Log Reader Agent) |
| &nbsp; | 変更データ キャプチャ (CDC) |
| &nbsp; | 管理対象のバックアップ |
| **高可用性** | データベース ミラーリング  |
| **Security** | 拡張キー管理 |
| &nbsp; | リンクサーバーの AD 認証 | 
| &nbsp; | 可用性グループの AD 認証 (Ag) | 
| &nbsp; | サードパーティ AD tools (Centrify、Vintela、Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | R services の SQL Server |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |
| &nbsp; | 分散トランザクションコーディネーター (DTC) |

## <a name="known-issues"></a>既知の問題

以下のセクションでは、Linux 上のの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]一般公開 (GA) リリースに関する既知の問題について説明します。

#### <a name="general"></a>全般

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]がインストールされているホスト名の長さは15文字以下でなければなりません。 

    - **解決策**:/Etc/hostname の名前を15文字以下に変更します。

- システム時刻[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を手動で設定すると、で内部システム[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時刻の更新が停止します。

    - **解決策**:[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を再起動します。

- 1つのインスタンスのインストールのみがサポートされています。

    - **解決策**:特定のホストに複数のインスタンスを作成する場合は、Vm または Docker コンテナーの使用を検討してください。 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Configuration Manager は、Linux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上のに接続できません。

- **Sa**ログインの既定の言語は英語です。

    - **解決策**:**ALTER login**ステートメントを使用して、 **sa**ログインの言語を変更します。

#### <a name="databases"></a>データベース

- Master データベースは mssql-conf ユーティリティを使用して移動することはできません。 他のシステムデータベースは mssql-conf で移動できます。

- Windows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でバックアップされたデータベースを復元する場合は、transact-sql ステートメントで**WITH MOVE**句を使用する必要があります。

- Microsoft 分散トランザクションコーディネーターサービスを必要とする分散トランザクションは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Linux での実行ではサポートされていません。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]リンク[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サーバーへの接続は、DTC が関係している場合を除き、サポートされます。 詳細については、「 [Microsoft 分散トランザクションコーディネーターサービスを必要とする分散トランザクションは、Linux で実行されている SQL Server ではサポートされません](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/)。」を参照してください。

- トランスポート層セキュリティ (TLS) の特定のアルゴリズム (暗号スイート) は、Linux 上[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のでは正常に機能しません。 この結果、に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]接続しようとすると接続エラーが発生し、高可用性グループのレプリカ間の接続を確立する際に問題が発生します。

   - **解決策**:次の手順を実行して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Linux 上のの mssql 構成スクリプトを変更して、問題のある暗号スイートを無効にします。

      1. /Var/opt/mssql/mssql.conf. に次のを追加します。

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. 次[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のコマンドを使用して再起動します。

      ```bash
      sudo systemctl restart mssql-server
      ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]インメモリ OLTP を使用する Windows 上のデータベースを、Linux [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]上ので復元することはできません。 インメモリ OLTP [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]を使用するデータベースを復元するには、最初にデータベース[!INCLUDE[ssSQL15](../includes/sssql15-md.md)]を[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]または Windows 上にアップグレード[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]してから、バックアップ/復元またはデタッチ/アタッチを使用して Linux 上でに移動します。

- 現時点では、ユーザーアクセス許可の**一括操作の管理**は、Linux ではサポートされていません。

#### <a name="networking"></a>ネットワーク

次の両方の条件が満たされている場合、リンクサーバーや可用性グループなど、sqlservr.exe プロセスからの送信 TCP 接続に関連する機能が動作しない可能性があります。

1. ターゲットサーバーは、IP アドレスではなく、ホスト名として指定されます。

1. ソースインスタンスは、カーネルで IPv6 を無効にしています。 システムでカーネルに IPv6 が有効になっているかどうかを確認するには、次のすべてのテストに合格する必要があります。

   - `cat /proc/cmdline`は、現在のカーネルのブート cmdline を出力します。 出力にを含める`ipv6.disable=1`ことはできません。
   - /Proc/sys/net/ipv6/ディレクトリが存在している必要があります。
   - を呼び出す`socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` C プログラムは成功する必要があります。 syscall は、fd! =-1 を返す必要があります。 eafnosupport では失敗しません。

正確なエラーは、機能によって異なります。 リンクサーバーの場合、このマニフェストはログインタイムアウトエラーとして使用されます。 可用性グループの場合、 `ALTER AVAILABILITY GROUP JOIN`セカンダリの DDL は5分後に失敗し、ダウンロード構成のタイムアウトエラーが発生します。

この問題を回避するには、次のいずれかの操作を行います。

1. TCP 接続のターゲットを指定するには、ホスト名ではなく Ip を使用します。

1. ブート cmdline からを削除`ipv6.disable=1`して、カーネルで IPv6 を有効にします。 これを行う方法は、Linux ディストリビューションとブートローダー (grub など) によって異なります。 IPv6 を無効にする場合でも、 `net.ipv6.conf.all.disable_ipv6 = 1` `sysctl`構成でを設定することによって無効にする`/etc/sysctl.conf`ことができます (例)。 これにより、システムのネットワークアダプターが IPv6 アドレスを取得できなくなりますが、sqlservr.exe の機能を使用できます。

#### <a name="network-file-system-nfs"></a>ネットワークファイルシステム (NFS)
**ネットワークファイルシステム (NFS)** のリモート共有を運用環境で使用する場合は、次のサポート要件に注意してください。

- NFS バージョン**4.2 以降**を使用します。 以前のバージョンの NFS では、最新のファイルシステムに共通する fallocate やスパースファイルの作成など、必要な機能がサポートされていません。
- NFS マウントで **/var/opt/mssql**ディレクトリのみを検索します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]システムバイナリなどの他のファイルはサポートされていません。
- リモート共有をマウントするときに NFS クライアントが ' nolock ' オプションを使用していることを確認します。

#### <a name="localization"></a>ローカリゼーション

- セットアップ中にロケールが英語 (en_us) でない場合は、bash セッション/ターミナルで UTF-8 エンコードを使用する必要があります。 ASCII エンコードを使用すると、次のようなエラーが表示される場合があります。

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   UTF-8 エンコードを使用できない場合は、MSSQL_LCID 環境変数を使用してセットアップを実行し、選択した言語を指定します。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Mssql-conf セットアップを実行していて、英語以外のの[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インストールを実行すると、ローカライズされたテキストの後に "構成 SQL Server..." という不適切な拡張文字が表示されます。 または、ラテン語以外のインストールの場合、文が完全に欠落している可能性があります。 見つからない文には、次のローカライズされた文字列が表示されます。"ライセンス PID が正常に処理されました。 新しいエディションは [\<Name\> edition] "です。 この文字列は情報だけを目的として出力さ[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]れ、次の累積的な更新プログラムでは、すべての言語でこの値に対応します。 これは、の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]正常なインストールには影響しません。 

#### <a name="full-text-search"></a>フルテキスト検索

- このリリースでは、Office ドキュメントのフィルターを含め、すべてのフィルターが使用できるわけではありません。 サポートされているフィルターの一覧については、 [Linux でのフルテキスト検索のインストール SQL Server](sql-server-linux-setup-full-text-search.md#filters)を参照してください。

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- **Mssql-server-is**パッケージは、このリリースの SUSE ではサポートされていません。 現時点では、Ubuntu と Red Hat Enterprise Linux (RHEL) でサポートされています。

- Linux CTP 2.1 更新以降では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]パッケージは linux で ODBC 接続を使用できます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]と MySQL odbc ドライバーを使用してテストされていますが、odbc 仕様を監視するすべての Unicode odbc ドライバーで動作することも想定されています。 デザイン時に、DSN または接続文字列を指定して ODBC データに接続することができます。Windows 認証を使用することもできます。 詳細については、「 [Linux での ODBC サポートの発表」ブログの投稿](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)を参照してください。

- Linux で SSIS パッケージを実行する場合、このリリースでは次の機能はサポートされていません。
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]カタログデータベース
  - SQL エージェントによるスケジュールされたパッケージの実行
  - [Windows 認証]
  - サードパーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Scale Out
  - SSIS 用 Azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

現在サポートされていない、または制限付きでサポートされている組み込み SSIS コンポーネントの一覧については、「 [Linux での ssis の制限事項と既知の問題](sql-server-linux-ssis-known-issues.md#components)」を参照してください。

Linux での SSIS の詳細については、次の記事を参照してください。
-   [Linux の SSIS サポートを発表するブログ記事](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)です。
-   [Linux に SQL Server Integration Services (SSIS) をインストールする](sql-server-linux-setup-ssis.md)
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

Linux 上のに[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]接続されている Windows のには、次の制限事項が適用されます。

- メンテナンスプランはサポートされていません。

- の[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]管理データウェアハウス (.mdw) とデータコレクターはサポートされていません。 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Windows 認証または Windows イベントログオプションを使用する UI コンポーネントは、Linux では機能しません。 これらの機能は、SQL ログインなどの他のオプションと共に使用することもできます。 

- 保持するログファイルの数を変更することはできません。

## <a name="next-steps"></a>次の手順

開始するには、次のクイックスタートを参照してください。

- [Red Hat Enterprise Linux にインストールする](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行する](quickstart-install-connect-ubuntu.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [実行と接続 - クラウド](quickstart-install-connect-clouds.md)

よく寄せられる質問への回答については、 [SQL SERVER ON LINUX FAQ](sql-server-linux-faq.md)を参照してください。
