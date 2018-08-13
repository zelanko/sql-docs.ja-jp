---
title: インターネットへのアクセスなしの SQL Server machine learning コンポーネントのインストール |マイクロソフトのドキュメント
description: オフラインまたは未接続 Machine Learning R および Pytyon セットアップ分離の SQL Server インスタンスにします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 56624d2a5fcc97035f434cb1ee1d4fdee4dedeba
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39546262"
---
# <a name="install-sql-server-machine-learning-r-and-python-features-on-computers-with-no-internet-access"></a>SQL Server コンピューターがインターネットにアクセスできないコンピューターで R と Python の機能の学習のインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

既定では、インストーラーが必要なを取得する、Microsoft ダウンロード サイトに接続しての更新されたコンポーネントでの機械学習 SQL Server。 ファイアウォールの制約は、これらのサイトからインストーラーを防ぐため場合、は、ファイルをダウンロード、サーバーがオフラインにファイルを転送し、セットアップを実行して、インターネットに接続されたデバイスを使用できます。

データベース内分析は、データベース エンジンのインスタンスと SQL Server のバージョンに応じて、R と Python の統合のための追加のコンポーネントで構成されます。 

+ SQL Server 2017 には、R と Python が含まれています。 
+ SQL Server 2016 は R のみです。 

分離されたサーバーで、CAB ファイルを machine learning と R および Python 言語固有の機能が追加されます。 

## <a name="sql-server-2017-offline-install"></a>SQL Server 2017 のオフライン インストール

独立したサーバー上の SQL Server 2017 Machine Learning サービス (R および Python) をインストールするには、SQL Server の最初のリリースをダウンロードして起動し、R と Python の対応する CAB ファイルのサポートします。 最新の累積的な更新プログラムを使用するようにサーバーをすぐに更新する場合でも、最初のリリースが最初にインストールする必要があります。

> [!Note]
> SQL Server 2017 には、サービス パックがありません。 累積的更新プログラムのみをサービスで、唯一のベース ラインとして初期リリースを使用する SQL Server の最初のリリースになります。 

### <a name="1---download-2017-cabs"></a>1-2017 の cab ファイルをダウンロードします。

コンピューターでインターネット接続には、SQL Server 2017 の最初のリリースと、インストール メディアの R と Python の機能を提供する CAB ファイルをダウンロードします。 

リリース  |ダウンロード リンク  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft Python のオープン     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python サーバー    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2-SQL Server 2017 インストール メディアを取得します。

1. インターネット接続を持つコンピューターで、ダウンロード、 [SQL Server 2017 セットアップ プログラム](https://www.microsoft.com/sql-server/sql-server-downloads)します。 

2. セットアップをダブルクリックし、選択、**ダウンロード メディア**インストールの種類。 このオプションでは、セットアップには、インストール メディアを含むローカル .iso (または .cab) ファイルが作成されます。

   ![ダウンロードのメディアのインストールの種類を選択](media/offline-download-tile.png "メディアのダウンロード")

## <a name="sql-server-2016-offline-install"></a>SQL Server 2016 のオフライン インストール

SQL Server 2016 データベース内分析は CAB が製品のパッケージと、オープン ソース R の Microsoft のディストリビューションのそれぞれファイル R 専用で、2 つだけです。 これらのリリースのいずれかをインストールすることによって開始: RTM、SP 1 では、SP 2。 適切な基本のインストールを行った後は、次の手順として累積的更新プログラムを適用できます。

コンピューターでインターネット接続には、データベース内分析を SQL Server 2016 をインストールするセットアップで使用される CAB ファイルをダウンロードします。 

### <a name="1---download-2016-cabs"></a>1-2016 cab ファイルをダウンロードします。

リリース  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP 2**  |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038) |

### <a name="2---get-sql-server-2016-installation-media"></a>2-SQL Server 2016 のインストール メディアを取得します。

SQL Server 2016 RTM、SP 1、または SP 2 は、ターゲット コンピューターで、最初のインストールとしてインストールできます。 これらのバージョンのいずれかには、累積的な更新が可能です。

.Iso ファイルを移動する方法の 1 つでは、インストール メディアを格納している[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)します。 サインインしてから、**ダウンロード**をインストールする SQL Server 2016 のリリースを検索するリンク。 ダウンロードは、オフライン インストール用のターゲット コンピューターにコピーすることができる .iso ファイルの形式です。

## <a name="transfer-files"></a>ファイルを転送します。

対象のコンピュータに SQL Server インストール メディア (.iso または .cab) とデータベース内分析 CAB ファイルをコピーします。 など、ターゲット マシン上の同じフォルダーに CAB ファイルとインストール メディアのファイルを配置**ダウンロード**またはセットアップのユーザーの temp * フォルダー。

次のスクリーン ショットでは、SQL Server 2017 の cab ファイルと ISO ファイルが表示されます。 SQL Server 2016 のダウンロードが異なって: ファイルの数を減らして (なしの Python) と、インストール メディアのファイル名は、2016年の。

![転送するファイルの一覧](media/offline-file-list.png "ファイルの一覧")

## <a name="run-setup"></a>セットアップの実行

セットアップを追加、インターネットから切断されているコンピューターで SQL Server セットアップを実行すると、**オフライン インストール**前の手順でコピーして CAB ファイルの場所を指定できるように、ウィザードのページします。

1. インストールを開始するには、インストール メディアにアクセスする .iso または .cab ファイルをダブルクリックします。 表示する必要があります、 **setup.exe**ファイル。

2. 右クリックして**setup.exe**管理者として実行します。

3. セットアップ ウィザードでは、オープン ソース R または Python コンポーネントのライセンス ページが表示されたら、クリックして**Accept**します。 ライセンス条項への同意を使用すると、次の手順に進むことができます。

4. 取得するときに、**オフライン インストール**] ページの [**インストール パス**、先ほどコピーした CAB ファイルを含むフォルダーを指定します。

   ![Cab フォルダーの選択ウィザード ページ](media/screenshot-sql-offline-cab-page.png "CAB フォルダー")

5. 引き続き次の画面に表示されるインストールを完了するように求められます。

## <a name="post-install-configuration"></a>インストール後の構成

インストールが完了すると、サービスを再起動し、スクリプトの実行を有効にするサーバーを構成します。

+ [外部スクリプトの実行 (SQL Server 2017) を有効にします。](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)
+ [外部スクリプトの実行 (SQL Server 2016) を有効にします。](sql-r-services-windows-install.md#bkmk_enableFeature)

SQL Server 2017 Machine Learning Services または SQL Server 2016 R Services のいずれかの初期のオフライン インストールでは、オンラインのインストールと同じ構成が必要です。

+ [インストールの確認](sql-machine-learning-services-windows-install.md#verify-installation)(SQL Server 2016 では、次のようにクリックします。[ここ](sql-r-services-windows-install.md#verify-installation))。
+ [必要に応じて追加の構成](sql-machine-learning-services-windows-install.md#additional-configuration)(SQL Server 2016 では、次のようにクリックします。[ここ](sql-r-services-windows-install.md#bkmk_FollowUp))。

<a name="slipstream-upgrades"></a>

## <a name="slipstream-upgrades"></a>スリップ ストリーム アップグレード

スリップストリーム セットアップとは、問題のあるインスタンスのインストールに修正プログラムまたは更新プログラムを適用して、既存の問題を修復する機能を指します。 この方法の利点は、SQL Server がセットアップの実行と同時に更新されるため、後で別途再起動する必要がないことです。

更新済みの SQL Server をダウンロードして、サービスの更新プログラムが適用されるサーバーがインターネットへのアクセスがあるない場合にインストーラーと対応するバージョンの言語に固有の CAB ファイル。 

1. ベースラインのインスタンスを起動します。 SQL Server のこれらのリリースでは、スリップ ストリーム アップグレードがサポートされています。

  + SQL Server 2017 の最初のリリース
  + SQL Server 2016 の初期リリース
  + SQL Server 2016 SP 1
  + SQL Server 2016 SP 2

2. 指定された累積的な更新プログラムの SQL Server インストーラーの更新バージョンを取得します。 Machine learning (R および Python) 機能への更新では、基になるデータベース エンジン インスタンスの累積更新プログラムと連携しています。

  + [SQL Server 2016 更新プログラム](https://sqlserverupdates.com/sql-server-2016-updates/)
  + [SQL Server 2017 更新プログラム](https://sqlserverupdates.com/sql-server-2017-updates/)

3. R と Python の対応する CAB ファイルを取得します。 ダウンロード リンクは、次を参照してください。[インスタンス SQL Server データベース内分析に累積的更新プログラム用 CAB のダウンロード](sql-ml-cab-downloads.md)します。

4. セットアップを実行、同じフォルダー内のすべてのファイルを配置します。 インストール中に、更新済みの CAB ファイルのフォルダーの場所の選択を求められます。

## <a name="next-steps"></a>次のステップ

インスタンスのインストール状態を確認し、一般的な問題を修正を参照してください。 [for SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)します。

不明なメッセージやログ エントリのすべてのヘルプを参照してください。[アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)します。

