---
title: Linux 上の SQL Server 2019 プレビューのリリース ノート |Microsoft Docs
description: この記事には、リリース ノートとサポートされる Linux で実行されている SQL Server 2019 プレビュー機能が含まれています。 リリース ノートは、この最新リリースと以前のリリースをいくつか含まれています。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4b6a8cb48e6447992fafc5b028146955668a7f66
ms.sourcegitcommit: 65ceea905030582f8d89e75e97758abf3b1f0bd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67399979"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Linux 上の SQL Server 2019 preview リリース ノート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

次のリリース ノートは、Linux で実行されている SQL Server 2019 プレビューに適用されます。 この記事では、各リリースについてのセクションに分割されます。 各リリースでは、CU 変更と、Linux のパッケージのダウンロードへのリンクを記述するサポートの記事にリンクがあります。

> [!TIP]
> SQL Server 2019 Linux の新機能については、次を参照してください。[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux)します。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3、7.4、7.5、または 7.6 Server | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| Docker エンジン 1.8 + では、Windows、Mac、または Linux | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!TIP]
> 詳細については、確認、[システム要件](sql-server-linux-setup.md#system)SQL Server on Linux の。 SQL Server 2017 の最新のサポート ポリシーで、次を参照してください。、 [for Microsoft SQL Server のテクニカル サポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)します。

## <a name="tools"></a>ツール

SQL Server を対象とするほとんどの既存クライアント ツールは、Linux で実行されている SQL Server を対象にシームレスにできます。 いくつかのツールは、Linux で機能する特定のバージョン要件があります。 SQL Server ツールの一覧については、次を参照してください。 [SQL Server の SQL ツールとユーティリティ](../tools/overview-sql-tools.md)します。

## <a name="release-history"></a>リリース履歴

次の表は、SQL Server 2019 プレビューの CTP リリースのリリース履歴を一覧表示します。

| リリース               | バージョン       | リリース日 |
|-----------------------|---------------|--------------|
| [CTP 3.1](#CTP31)     | 15.0.1700.37  | 2019-6-26    |
| [CTP 3.0](#CTP30)     | 15.0.1600.8   | 2019-5-22    |
| [CTP 2.5](#CTP25)     | 15.0.1500.28  | 2019-4-24    |
| [CTP 2.4](#CTP24)     | 15.0.1400.75  | 2019-3-27    |
| [CTP 2.3](#CTP23)     | 15.0.1300.359 | 2019-3-01    |
| [CTP 2.2](#CTP22)     | 15.0.1200.24  | 2018-12-11   |
| [CTP 2.1](#CTP21)     | 15.0.1100.94  | 2018-11-06   |
| [CTP 2.0](#CTP20)     | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> 更新プログラムをインストールする方法

プレビューのリポジトリを構成している場合 (**mssql-サーバー-プレビュー**)、新規インストールを実行すると、最新の SQL Server CTP パッケージが表示されます。 Docker コンテナー イメージを必要とする場合の公式イメージを参照してください[Microsoft SQL Server on Linux 上の Docker エンジン](https://hub.docker.com/r/microsoft/mssql-server/)します。 リポジトリの構成の詳細については、次を参照してください。[リポジトリを構成する SQL Server on Linux の](sql-server-linux-change-repo.md)します。

SQL Server の既存のパッケージを更新する場合は、最新の CU を取得するには、各パッケージの適切な更新プログラムのコマンドを実行します。 各パッケージの特定の更新手順については、次のインストール ガイドを参照してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md#upgrade)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)
- [Linux 上の SQL Server 2019 プレビューの Machine Learning サービスの R と Python のサポートをインストールします。](sql-server-linux-setup-machine-learning.md)
- [PolyBase のパッケージをインストールします。](../relational-databases/polybase/polybase-linux-setup.md)
- [SQL Server エージェントを有効にします。](sql-server-linux-setup-sql-agent.md)

## <a id="CTP31"></a> CTP 3.1 (2019年 6 月)

次のセクションでは、パッケージの場所を提供し、CTP 3.1 の既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1700.37-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1700.37-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1700.37-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1700.37-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1700.37-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1700.37-2_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1700.37-2_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1700.37-2_amd64.deb)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1700.37-2_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a id="msdtc"></a> Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP30"></a> CTP 3.0 (月 2019)

次のセクションでは、パッケージの場所を提供し、CTP 3.0 に関する既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1600.8-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1600.8-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1600.8-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1600.8-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1600.8-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1600.8-1_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1600.8-1_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1600.8-1_amd64.deb)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1600.8-1_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a id="msdtc"></a> Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP25"></a> CTP 2.5 (Apr 2019)

次のセクションでは、パッケージの場所を指定して、リリースの CTP 2.5 の既知の問題。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1500.28-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1500.28-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1500.28-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1500.28-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1500.28-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1500.28-1_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1500.28-1_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1500.28-1_amd64.deb)</br>[PolyBase の RPM パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1500.28-1_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a id="msdtc"></a> Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP24"></a> CTP 2.4 (Mar 2019)

次のセクションでは、パッケージの場所を提供し、CTP 2.4 の既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1400.75-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1400.75-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1400.75-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a id="msdtc"></a> Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP23"></a> CTP 2.3 (Feb 2019)

次のセクションでは、パッケージの場所を提供し、CTP 2.3 に関する既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1300.359-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1300.359-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1300.359-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a id="msdtc"></a> Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP22"></a> CTP 2.2 (12/2018)

次のセクションでは、パッケージの場所を提供し、CTP 2.2 の既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1200.24-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1200.24-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1200.24-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a id="msdtc"></a> Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP21"></a> CTP 2.1 (2018 の年 11 月)

次のセクションでは、パッケージの場所を提供し、CTP 2.1 の既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1100.94-1 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1100.94-1 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1100.94-1 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a id="CTP20"></a> CTP 2.0 (2018年 9 月)

次のセクションでは、パッケージの場所を提供し、CTP 2.0 の既知の問題を離します。 SQL Server 2019 上の Linux の新機能の詳細については、次を参照してください。、[新機能については SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)します。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 15.0.1000.34-2 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| SLES RPM パッケージ | 15.0.1000.34-2 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Java の機能拡張の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Debian パッケージを Ubuntu 16.04 | 15.0.1000.34-2 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Debian パッケージの機能拡張](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Java の機能拡張の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>既知の問題

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft 分散トランザクション コーディネーター

現時点では、MSDTC では、認証できないトランザクションが必要です。 たとえばで Windows SQL Server on Linux に SQL Server からのリンク サーバーを使用している Windows クライアント アプリケーションを使用して Linux 上の SQL Server に対して分散トランザクションを開始するか、し、Windows サーバー/クライアントの MSDTC は"No オプションを使用するために必要認証が必要です"。

## <a name="next-steps"></a>次のステップ

開始するには、次のクイック スタートを参照してください。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [実行と接続 - クラウド](quickstart-install-connect-clouds.md)

よく寄せられる質問の回答は、次を参照してください。、 [SQL Server on Linux の FAQ](sql-server-linux-faq.md)します。
