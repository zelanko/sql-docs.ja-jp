---
title: Linux 上の SQL Server 2017 のリリース ノート |Microsoft Docs
description: この記事では、リリース ノートが含まれていて、Linux で実行されている SQL Server 2017 の機能がサポートされています。 リリース ノートは、この最新リリースと以前のリリースをいくつか含まれています。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/25/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: e272187ae3e634246f9f32323438d81d633c3fbc
ms.sourcegitcommit: 8aa51bc0bc54b266145c96f6451b59f369822160
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66036913"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 のリリース ノート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次のリリース ノートに適用されます[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]Linux で実行されています。 この記事では、各リリースについてのセクションに分割されます。 GA リリースがサポートの詳細し、既知の問題が一覧表示します。 各累積更新プログラム (CU) または一般配布リリース (GDR) CU 変更と、Linux のパッケージのダウンロードへのリンクを記述するサポートの記事にリンクがあります。

> [!TIP]
> これらのリリース ノートを目的と[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]を解放します。 詳細については、新しい[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]を参照してください[Linux 上の SQL Server 2019 プレビューのリリース ノート](sql-server-linux-release-notes-2019.md?view=sql-server-ver15)します。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3、7.4、7.5、または 7.6 Server | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| Docker エンジン 1.8 + では、Windows、Mac、または Linux | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!TIP]
> 詳細については、確認、[システム要件](sql-server-linux-setup.md#system)の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 最新のサポート ポリシーの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]を参照してください、 [for Microsoft SQL Server のテクニカル サポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)します。

## <a name="tools"></a>ツール

既存のほとんどのクライアント ツールの対象とする[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を対象にシームレスに[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux で実行されています。 いくつかのツールは、Linux で機能する特定のバージョン要件があります。 完全な一覧については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ツールを参照してください[SQL Server の SQL ツールとユーティリティ](../tools/overview-sql-tools.md)します。

## <a name="release-history"></a>リリース履歴

次の表のリリース履歴[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。

| リリース               | バージョン       | リリース日 |
|-----------------------|---------------|--------------|
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

## <a id="cuinstall"></a> 更新プログラムをインストールする方法

CU リポジトリを構成している場合 (**mssql server-2017**) の最新の CU が表示されます[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]新規インストールを実行するときにパッケージ化します。 すべてのパッケージのインストールのアーティクルの既定値です CU リポジトリ[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 GDR のリポジトリを構成している場合 (**mssql server 2017 gdr**)、一般以降にリリースされた重要なセキュリティ更新プログラムのみが取得されます Docker コンテナー CU または GDR 更新プログラムが必要な場合の公式イメージを参照してください[Microsoft SQL Server on Linux 上の Docker エンジン](https://hub.docker.com/r/microsoft/mssql-server)します。 リポジトリの構成の詳細については、次を参照してください。[リポジトリを構成する SQL Server on Linux の](sql-server-linux-change-repo.md)します。

既存の更新する場合は[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]パッケージが最新の CU を取得するには、各パッケージの適切な更新プログラムのコマンドを実行します。 各パッケージの特定の更新手順については、次のインストール ガイドを参照してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md#upgrade)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)
- [SQL Server エージェントを有効にします。](sql-server-linux-setup-sql-agent.md)

## <a id="CU14"></a> CU14 (2018 の年 3 月)

これは、累積的な更新プログラムの 14 (CU14) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3076.1 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4484710](https://support.microsoft.com/help/4484710)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3076.1-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3076.1-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3076.1-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a> CU13 (12/2018)

これは、累積的な更新プログラム 13 (CU13) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3048.4 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4466404](https://support.microsoft.com/help/4466404)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3048.4-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3048.4-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3048.4-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a> CU12 (Oct 2018)

これは、Cumulative Update 12 (CU12) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3045.24 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4464082](https://support.microsoft.com/help/4464082)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3045.24-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3045.24-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3045.24-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a> CU11 (2018年 9 月)

これは、累積的な更新プログラム 11 (CU11) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3038.14 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4462262](https://support.microsoft.com/help/4462262)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3038.14-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3038.14-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3038.14-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a> CU10 (Aug 2018)

これは、Cumulative Update 10 (CU10) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3037.1 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4342123](https://support.microsoft.com/help/4342123)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3037.1-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3037.1-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3037.1-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a> CU9 GDR2 (Aug 2018)

以前にリリースされた CU (CU9) 含まれており、セキュリティ更新プログラムが、この[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3035.2 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4293805](https://support.microsoft.com/help/4293805)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3035.2-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| SLES RPM パッケージ | 14.0.3035.2-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3035.2-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a> GDR2 (Aug 2018)

これは、GDR2 (および GDR1) に対するセキュリティ更新プログラムのみを含むセキュリティ更新プログラム[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。  [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.2002.14 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4293803](https://support.microsoft.com/help/4293803)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.2002.14-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.2002.14-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.2002.14-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a> CU9 (2018 年 7 月)

これは、累積的な更新プログラム 9 (CU9) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3030.27 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4341265](https://support.microsoft.com/help/4341265)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3030.27-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3030.27-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3030.27-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a> CU8 (Jun 2018)

これは、累積的な更新プログラム 8 (CU8) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3029.16 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4338363](https://support.microsoft.com/help/4338363)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3029.16-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3029.16-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3029.16-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> CU7 (2018 年 5 月)

これは、累積的な更新プログラム 7 (CU7) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3026.27 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4229789](https://support.microsoft.com/help/4229789)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3026.27-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3026.27-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3026.27-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (Apr 2018)

これは、累積的な更新プログラム 6 (CU6) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3025.34 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3025.34-3 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3025.34-3 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3025.34-3 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (2018 の年 3 月)

これは、累積的な更新プログラム 5 (CU5) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3023.8 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4092643](https://support.microsoft.com/help/4092643)します。

### <a name="known-upgrade-issue"></a>アップグレードの既知の問題

以前のリリースから CU5 にアップグレードするときに[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が次のエラーで起動に失敗します。

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

このエラーを解決するには、SQL Server エージェントを有効にし、再起動[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]次のコマンドを使用します。

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3023.8-5 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3023.8-5 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3023.8-5 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> CU4 (Feb 2018)

これは、Cumulative Update 4 (CU4) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3022.28 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4056498](https://support.microsoft.com/help/4056498)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

> [!NOTE]
> CU4、時点で別のパッケージとして、SQL Server エージェントはインストールできません。 エンジン パッケージと共にインストールされ、有効にする必要があります。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3022.28-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3022.28-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3022.28-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a> GDR1 (Jan 2018)

これは、セキュリティ更新プログラムのセキュリティ修正プログラムを GDR1 のみを含む[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.2000.63 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4057122](https://support.microsoft.com/help/4057122)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.2000.63-3 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.2000.63-3 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.2000.63-3 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a> CU3 (Jan 2018)

これは、累積更新プログラム 3 (CU3) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3015.40 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4052987](https://support.microsoft.com/help/4052987)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3015.40-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3015.40-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3015.40-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> CU2 (2017 年 11 月)

これは、Cumulative Update 2 (CU2) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3008.27 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3008.27-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3008.27-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3008.27-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (Oct 2017)

これは、Cumulative Update 1 (CU1) のリリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.3006.16 します。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/KB4053439](https://support.microsoft.com/help/4038634)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3006.16-3 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3006.16-3 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.3006.16-3 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> GA (Oct 2017)

これは、一般公開 (GA) リリースの[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]します。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]このリリースのバージョン番号は 14.0.1000.169 します。

### <a name="package-details"></a>パッケージの詳細

パッケージの詳細と、RPM および Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合は、これらのパッケージを直接ダウンロードする必要がないことに注意してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.1000.169-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.1000.169-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server エージェントの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Debian パッケージを Ubuntu 16.04 | 14.0.1000.169-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> サポートされていない機能とサービス

次の機能とサービスは、GA リリースの時点では Linux で使用できません。 これらの機能のサポートは、時間の経過と共にますます有効になります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | トランザクション レプリケーション |
| &nbsp; | マージ レプリケーション |
| &nbsp; | Change Data Capture (SQL Server エージェントを参照してください) |
| &nbsp; | Stretch DB |
| &nbsp; | PolyBase |
| &nbsp; | サード パーティ製接続を使用した分散クエリ |
| &nbsp; | 以外のデータ ソースへのリンク サーバー [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable は、FILESTREAM |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| &nbsp; | バッファー プール拡張 |
| **SQL Server エージェント** |  サブシステム:CmdExec、PowerShell、キュー リーダー、SSIS、SSAS、SSRS |
| &nbsp; | オブジェクト エクスプローラーには |
| &nbsp; | ログ リーダー エージェント (Log Reader Agent) |
| &nbsp; | 変更データ キャプチャ (CDC) |
| &nbsp; | 管理対象のバックアップ |
| **高可用性** | データベース ミラーリング  |
| **Security** | 拡張キー管理 |
| &nbsp; | リンク サーバーの AD 認証 | 
| &nbsp; | 可用性グループ (Ag) に対して AD 認証 | 
| &nbsp; | AD のサードパーティ ツール (Centrify、いる Vintela、Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |
| &nbsp; | 分散トランザクション コーディネーター (DTC) |

## <a name="known-issues"></a>既知の問題

次のセクションでは、一般公開 (GA) リリースの既知の問題を説明する[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]Linux 上。

#### <a name="general"></a>全般

- ホスト名の長さ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が 15 文字にする必要があるインストールされている以下。 

    - **解像度**:何か 15 文字以下に/etc/hostname 内の名前を変更します。

- システム時刻を時に旧バージョンと手動で設定すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]内での内部のシステム時刻の更新を停止する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]します。

    - **解像度**:[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を再起動します。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**:特定のホストでは、複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナー。 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager に接続できません[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。

- 既定の言語、 **sa**ログインは英語です。

    - **解像度**:言語を変更、 **sa**でのログイン、 **ALTER LOGIN**ステートメント。

#### <a name="databases"></a>データベース

- Mssql conf ユーティリティでは、master データベースを移動できません。 Mssql 会議で他のシステム データベースを移動できます。

- バックアップされたデータベースを復元するときに[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、Windows で使用する必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションがサポートされていない[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux で実行されています。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] DTC が含まれる場合を除き、リンク サーバーがサポートされています。 詳細については、次を参照してください。 [Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされません](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/)します。

- 特定のアルゴリズム (暗号スイート) トランスポート層セキュリティ (TLS) が正しく動作しない[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 接続するときに、接続エラー結果[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、高可用性グループ レプリカ間の接続の確立に問題とします。

   - **解像度**:変更、 **mssql.conf**用の構成スクリプト[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]on Linux は、次の手順を実行して問題のある暗号を無効にします。

      1. 次の/var/opt/mssql/mssql.conf に追加します。

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. 再起動[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]次のコマンドを使用します。

      ```bash
      sudo systemctl restart mssql-server
      ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] インメモリ OLTP を使用して Windows 上のデータベースを復元できません[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]Linux 上。 復元する、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]では、インメモリ OLTP を使用するデータベースが最初にデータベースをアップグレード[!INCLUDE[ssSQL15](../includes/sssql15-md.md)]または[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]上に移動する前に Windows[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]バックアップ/復元またはデタッチ/アタッチを使用して Linux 上。

- ユーザーのアクセス許可**ADMINISTER BULK OPERATIONS**この時点で、Linux でサポートされていません。

#### <a name="networking"></a>ネットワーク

次の両方の条件が満たされた場合、リンク サーバーなど、可用性グループ、sqlservr プロセスからの送信 TCP 接続に関連する機能は動作しない可能性があります。

1. ターゲット サーバーは、ホスト名と IP アドレスではなくとして指定されます。

1. ソース インスタンスが、IPv6、カーネルで無効になっています。 IPv6、カーネルで有効になっているがをシステムを確認するには、次のすべてのテストが渡す必要があります。

   - `cat /proc/cmdline` 現在のカーネルのブート cmdline が印刷されます。 出力にはする必要がありますが含まれていない`ipv6.disable=1`します。
   - Proc/sys]、[net ipv6/ディレクトリが存在する必要があります。
   - C プログラムを呼び出す`socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)`成功する必要があります - syscall が fd を返す必要があります! =-1 と EAFNOSUPPORT に失敗しません。

正確なエラーは、機能に依存します。 リンク サーバーでは、ログインのタイムアウト エラーとしてこのマニフェストします。 可用性グループの場合、`ALTER AVAILABILITY GROUP JOIN`ダウンロード構成のタイムアウト エラーで 5 分後に、セカンダリで DDL は失敗します。

この問題を回避するには、次のいずれかの操作を行います。

1. ホスト名ではなく ip アドレスを使用すると、TCP 接続のターゲットを指定します。

1. 削除することで、カーネルで IPv6 を有効にする`ipv6.disable=1`ブートするコマンドラインから。 これを行う方法は、Linux ディストリビューションと grub など、ブートローダーによって異なります。 IPv6 を無効にする場合、まだ無効にできますに設定して`net.ipv6.conf.all.disable_ipv6 = 1`で、`sysctl`構成 (例: `/etc/sysctl.conf`)。 これもこのメッセージは、システムのネットワーク アダプターが、IPv6 アドレスを取得しないようにするが、sqlservr 機能が動作しましょう。

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
使用する場合**Network File System (NFS)** 、運用環境でのリモート共有には、次のサポート要件に注意してください。

- NFS のバージョンを使用して**4.2 以上**します。 以前のバージョンの NFS は、fallocate スパース ファイルの作成、最新のファイル システムに共通してなどの必要な機能をサポートしません。
- のみを検索、 **/var/opt/mssql** NFS マウント上のディレクトリ。 などの他のファイル、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]システム バイナリがサポートされていません。
- NFS クライアントがリモート共有をマウントするときに、'nolock' オプションを使用することを確認します。

#### <a name="localization"></a>ローカリゼーション

- ロケールが英語 (en_us) のセットアップ中にでない場合は、bash セッション/ターミナルで utf-8 のエンコードを使用する必要があります。 ASCII エンコーディングを使用する場合は、次のようなエラーを参照してください可能性があります。

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Utf-8 エンコードを使用できない場合は、好みの言語を指定する MSSQL_LCID 環境変数を使用してセットアップを実行します。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Mssql conf のセットアップを実行している場合の英語以外のインストールを実行して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、不適切な拡張文字が「を構成する SQL Server…」ローカライズされたテキストの後に表示されます。 または、ベースのインストールをラテン語以外の場合、文が見つからないことが完全にします。 不足している文では、次のローカライズされた文字列を表示する必要があります。"ライセンス PID は正常に処理されました。 新しいエディションは [\<名前\>edition]"。 この文字列は、情報のみを目的として、次の出力は[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]累積更新プログラムはすべての言語のこれを解決します。 これには影響しませんが、正常にインストール[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]何らかの方法でします。 

#### <a name="full-text-search"></a>フルテキスト検索

- すべてのフィルターなどの Office ドキュメントのフィルターは、このリリースで利用できます。 サポートされているフィルターの一覧は、次を参照してください。 [on Linux SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)します。

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- **Mssql server は**パッケージは SUSE にこのリリースではサポートされません。 Ubuntu、Red Hat Enterprise Linux (RHEL) でこれ現在サポートされています。

- [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Linux CTP 2.1 の更新に関する以降[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]パッケージは Linux で ODBC 接続を使用することができます。 この機能がテストされている、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]および MySQL ODBC ドライバーが、ODBC 仕様には任意の Unicode ODBC ドライバーを使用することも必要です。 デザイン時に、DSN または接続文字列は、ODBC データに接続するを指定することができます。Windows 認証を使用することもできます。 詳細については、次を参照してください。、[ブログ Linux に ODBC サポートのお知らせを投稿する](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)します。

- Linux で SSIS パッケージを実行すると、このリリースでは、次の機能はサポートされていません。
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログ データベース
  - SQL エージェントでスケジュールされたパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] スケール アウト
  - Azure Feature Pack for SSIS
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

現在サポートされていない、または制限付きサポートされている組み込みの SSIS コンポーネントの一覧は、次を参照してください。[制限事項と既知の問題を Linux 上の SSIS の](sql-server-linux-ssis-known-issues.md#components)します。

Linux 上の SSIS の詳細については、次の記事を参照してください。
-   [Linux の SSIS サポート ブログの投稿のお知らせ](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)します。
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

次の制限が適用される[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]に接続されている Windows の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) およびデータ コレクターで[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]はサポートされていません。 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Windows 認証または Windows イベント ログのオプションを持つ UI コンポーネントは、Linux では動作しません。 SQL ログインなどの他のオプションを使用してこれらの機能を引き続き使用できます。 

- 保持するログ ファイルの数を変更できません。

## <a name="next-steps"></a>次の手順

開始するには、次のクイック スタートを参照してください。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [実行と接続 - クラウド](quickstart-install-connect-clouds.md)

よく寄せられる質問の回答は、次を参照してください。、 [SQL Server on Linux の FAQ](sql-server-linux-faq.md)します。
