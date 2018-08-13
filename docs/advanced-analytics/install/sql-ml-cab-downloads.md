---
title: CAB は、SQL Server の累積的更新プログラムのダウンロード |マイクロソフトのドキュメント
description: SQL Server 2017 Machine Learning Services と SQL Server 2016 R Services の CAB のダウンロード。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a2893e976e64315a1aad742062e962269439b72
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566319"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>インスタンスの SQL Server データベース内分析の累積的更新プログラム用 CAB のダウンロードします。

データベース内分析用に構成された SQL Server インスタンスには、CAB ファイル、インストールされ、サービスからの SQL Server セットアップに含まれている R と Python の機能が含まれます。 

インターネットに接続されているサーバーで、通常は Windows Update を通じてに CAB の更新が適用されます。 切断されたサーバーを手動で更新する必要があります。 この記事では、インターネットから切断されているサーバーを手動で更新できるように、SQL Server 2017 Machine Learning サービス (R および Python) または SQL Server 2016 R Services の各累積更新プログラム用の CAB ファイルのダウンロード リンクを提供します。 

## <a name="prerequisites"></a>前提条件

ベースライン インストールで開始します。

+ SQL Server 2017 Machine Learning Services では、最初のリリースは、基準インストールです。 

+ SQL Server 2016 R Services では、最初のリリース、SP1、または sp2 が適用を開始できます。 

詳細については、次を参照してください。 [SQL Server をインストールした機械学習のインターネット アクセスなしでコンポーネントを](sql-ml-component-install-without-internet-access.md)します。

ベースライン インストールしたらを実行できます、[アップグレード スリップ ストリーム](sql-ml-component-install-without-internet-access.md#slipstream-upgrades)CAB ファイルの更新された機械学習機能を含むです。

CAB ファイルは、逆時系列順に表示されます。 CAB ファイルをダウンロードしたり、ターゲット コンピューターに転送すると、フォルダーに配置する便利ななど**ダウンロード**またはセットアップのユーザーの %temp% フォルダー。

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 の cab ファイル

リリース  |ダウンロード リンク  |
---------|---------|
**SQL Server 2017 CU8-CU9** |
Microsoft R Open     |変更はありません。使用前[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Microsoft Python のオープン     |変更はありません。使用前[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Microsoft Python サーバー    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)]|
**SQL Server 2017 CU6-cu7 以降** |
Microsoft R Open     |変更はありません。使用前[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Microsoft Python のオープン     |変更はありません。使用前[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Microsoft Python サーバー    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**SQL Server 2017 CU5** |
Microsoft R Open     |変更はありません。使用前[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Microsoft Python のオープン     |変更はありません。使用前[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Microsoft Python サーバー    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**SQL Server 2017 CU4** |
Microsoft R Open     |変更はありません。使用前[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Microsoft Python のオープン     |変更はありません。使用前[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Microsoft Python サーバー    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Microsoft Python のオープン     |変更はありません。使用前[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Microsoft Python サーバー    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 CU1-CU2** |
Microsoft R Open     |変更はありません。使用前[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Microsoft Python のオープン     |変更はありません。使用前[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Microsoft Python サーバー    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 の最初のリリース** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft Python のオープン     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python サーバー    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 の cab ファイル

SQL Server 2016 R Services では、ベースライン リリースは、RTM バージョンまたは service pack のバージョンです。

リリース  |ダウンロード リンク  |
---------|---------------|
**SQL Server 2016 SP2 CU1-CU2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |変更はありません。使用前[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 CU1-CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)=
**SQL Server 2016 CU4-CU9**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU2-CU3**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)

> [!NOTE]
> 
> SQL Server 2016 SP1 CU4、または SP1 CU5 のオフライン インストール、SRO_3.2.2.16000_1033.cab をダウンロードします。 FWLINK 831785 から、[設定] ダイアログ ボックスに記載されている SRO_3.2.2.13000_1033.cab をダウンロードした場合は、累積更新プログラムをインストールする前に SRO_3.2.2.16000_1033.cab としてファイルを変更します。

.Tar 形式のアーカイブとしてダウンロードできますが、Microsoft R のソース コードを表示する場合は、: [R Server のダウンロードのインストーラー](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

# <a name="see-also"></a>参照

[SQL Server の学習インターネット アクセスのないコンポーネントのインストールします。](sql-ml-component-install-without-internet-access.md)
