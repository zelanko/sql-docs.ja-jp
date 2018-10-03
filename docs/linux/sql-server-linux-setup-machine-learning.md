---
title: Learning サービス (R、Python、Java) を Linux 上の SQL Server マシンのインストール |Microsoft Docs
description: この記事では、Red Hat、Ubuntu 上の SQL Server Machine Learning サービス (R、Python、Java) をインストールする方法を説明します。
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b61eb365cc818bafc3e0b584f91dd9e85b09cc24
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770940"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>SQL Server 2019 の Machine Learning サービス (R、Python、Java) Linux 上のインストールします。

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md)以降の SQL Server 2019 このプレビュー リリースでは Linux オペレーティング システム上で動作します。 Java プログラミング拡張機能、または R と Python の拡張機能を学習するコンピューターにインストールするには、この記事の手順に従います。 

機械学習やプログラミング拡張機能は、データベース エンジンへのアドオンです。 できますが、[データベース エンジンと Machine Learning サービスを同時にインストール](#install-all)、インストールして詳細を追加する前に、問題を解決できるように、まず、SQL Server データベース エンジンを構成することをお勧めコンポーネント。 

R、Python、および Java 拡張機能のパッケージの場所は、SQL Server Linux ソース リポジトリでいます。 既に構成されている場合は、ソース リポジトリ データベース エンジンのインストール、mssql mlservices 同じリポジトリの登録を使用してパッケージのインストール コマンドを実行できます。

## <a name="prerequisites"></a>前提条件

+ Linux オペレーティング システムである必要があります[SQL Server でサポートされている](sql-server-linux-release-notes-2019.md#supported-platforms)、オンプレミス、または Docker コンテナーで実行中です。

+ SQL Server 2019 データベース エンジンのインスタンスが必要です。 

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ のみ、R の[Microsoft R Open](#mro) mssql mlsservices R パッケージ。 

<a name="mro"></a>

### <a name="microsoft-r-open-mro"></a>Microsoft R Open (MRO)

Microsoft の基本ディストリビューションの R は、RevoScaleR、MicrosoftML、および Machine Learning サービスでインストールされているその他の R パッケージを使用するための前提条件です。

次のコマンドは、MRO を提供するリポジトリを登録します。 登録後、その他の R パッケージをインストールするためのコマンドにより、パッケージの依存関係として MRO は自動的に含めます。

#### <a name="on-ubuntu"></a>Ubuntu の場合

```bash
# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 18.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb
```

#### <a name="on-rhel"></a>RHEL で

```bash
# Set the location of the package repo at the "prod" directory
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm
```
#### <a name="on-suse"></a>SUSE に

```bash
# Set the location of the package repo
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com
```

## <a name="package-list"></a>パッケージの一覧

インターネットに接続されたデバイスで、パッケージがダウンロードされ、各オペレーティング システム、パッケージ インストーラーを使用して、データベース エンジンとは別にインストールされています。 次の表に、すべての利用可能なパッケージが、インターネットに接続されたインストールの場合、必要なだけ*1 つ*R または Python のパッケージを特定の機能の組み合わせを取得します。

| パッケージ名 | 適用先 | 説明 |
|--------------|----------|-------------|
|mssql-サーバーの機能拡張  | All | 機能拡張フレームワークが R、Python、または Java コードを実行するために使用します。 |
|mssql server extensibility java | Java | Java の実行環境を読み込むための Java 拡張機能。 その他のライブラリや Java のパッケージはありません。 |
| microsoft openmpi  | Python、R | メッセージは Linux での並列処理の Revo のライブラリによって使用されるインターフェイスを渡します。 |
| microsoft r のオープン | R | オープン ソース ディストリビューションは r です。 |
| mssql-mlservices-python | Python | Anaconda と Python のオープン ソース ディストリビューション。 |
|mssql mlservices mlm py  | Python | 完全をインストールします。 Revoscalepy、microsoftml、事前トレーニング済みの画像の特徴の生成とテキストのセンチメント分析のモデルを提供します。| 
|mssql mlservices mml py  | Python | 部分インストールします。 Revoscalepy、microsoftml を提供します。 <br/>事前トレーニング済みモデルを除外します。 | 
|mssql mlservices パッケージ py  | Python | 部分インストールします。 Revoscalepy を提供します。 <br/>事前トレーニング済みモデルと microsoftml を除外します。 | 
|mssql mlservices mlm r  | R | 完全をインストールします。 第 sqlRUtils RevoScaleR、MicrosoftML、olapR、事前トレーニング済みの画像の特徴の生成とテキストのセンチメント分析のモデルを提供します。| 
|mssql mlservices mml r  | R | 部分インストールします。 RevoScaleR、MicrosoftML、sqlRUtils、olapR を提供します。 <br/>事前トレーニング済みモデルを除外します。  |
|mssql mlservices パッケージ r  | R | 部分インストールします。 RevoScaleR、sqlRUtils、olapR を提供します。 <br/>事前トレーニング済みモデルと MicrosoftML を除外します。 | 

<a name="RHEL"></a>

## <a name="rhel-commands"></a>RHEL コマンド

いずれかがインストール*1 つ*R パッケージ、および*1 つ*Python パッケージ、および Java の場合、その機能を使用します。 各 R と Python のパッケージには、機能のバンドルが含まれています。 必要な機能セットを提供するパッケージを選択します。 依存パッケージが自動的に含まれます。

> [!Tip]
> 実行可能であれば、`yum clean all`をインストールする前に、システム上のパッケージを更新します。

### <a name="example-1----full-installation"></a>例 1: フル インストール 

R と Python のオープン ソース R および Python に extensibility framework、microsoft openmpi、拡張機能 (R、Python、Java) を machine learning ライブラリと事前トレーニング済みモデルが含まれています。 R と Python の完全なと最小のインストール - 機械学習ライブラリなどが、事前トレーニング済みモデルの間にある処理を行う場合に置き換えてください`mssql-mlservices-mml-r-9.4.5*`と`mssql-mlservices-mml-py-9.4.5*`代わりにします。

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.5*
sudo yum install mssql-mlservices-mlm-r-9.4.5* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>例 2: 最小インストール 

R、Python、Java の拡張機能のオープン ソース R および Python に extensibility framework、microsoft openmpi のコア Revo * ライブラリが含まれています。 事前トレーニング済みモデルと machine learning の R と Python ライブラリを除外します。 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.5*
sudo yum install mssql-mlservices-packages-r-9.4.5*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Ubuntu のコマンド

いずれかがインストール*1 つ*R パッケージ、および*1 つ*Python パッケージ、および Java の場合、その機能を使用します。 各 R と Python のパッケージには、機能のバンドルが含まれています。 必要な機能セットを提供するパッケージを選択します。 依存パッケージが自動的に含まれます。

> [!Tip]
> 実行可能であれば、`apt-get update`をインストールする前に、システム上のパッケージを更新します。 さらに、Ubuntu のいくつかの docker イメージでは、https の apt トランスポート オプションがあります。 これをインストールするには使用`apt-get install apt-transport-https`します。

### <a name="prerequisite-for-1804"></a>18.04 の前提条件

Ubuntu 18.04 上の mssql mlservices R ライブラリを実行する必要があります**libpng12** Linux カーネルにアーカイブします。 このパッケージは、標準の配布には含まれなくし、手動でインストールする必要があります。 このライブラリを取得するには、次のコマンドを実行します。

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-01_1.2.54-1ubuntu1_amd64.deb
```

### <a name="example-1----full-installation"></a>例 1: フル インストール 

R と Python のオープン ソース R および Python に extensibility framework、microsoft openmpi、拡張機能 (R、Python、Java) を machine learning ライブラリと事前トレーニング済みモデルが含まれています。 機械学習ライブラリなどが事前トレーニング済みモデル - - R、Python、フル インストール オプションと最小値の間に処理を行う場合インストール mssql mlservices mml r と mssql mlservices mml py を代わりに置き換えてください。

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>例 2: 最小インストール 

R、Python、Java の拡張機能のオープン ソース R および Python に extensibility framework、microsoft openmpi のコア Revo * ライブラリが含まれています。 事前トレーニング済みモデルと machine learning の R と Python ライブラリを除外します。 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

## <a name="suse-commands"></a>SUSE コマンド

いずれかがインストール*1 つ*R パッケージ、および*1 つ*Python パッケージ、および Java の場合、その機能を使用します。 各 R と Python のパッケージには、機能のバンドルが含まれています。 必要な機能セットを提供するパッケージを選択します。 依存パッケージが自動的に含まれます。 

### <a name="example-1----full-installation"></a>例 1: フル インストール 

R と Python のオープン ソース R および Python に extensibility framework、microsoft openmpi、拡張機能 (R、Python、Java) を machine learning ライブラリと事前トレーニング済みモデルが含まれています。 R と Python の完全なと最小のインストール - 機械学習ライブラリなどが、事前トレーニング済みモデルの間にある処理を行う場合に置き換えてください`mssql-mlservices-mml-r-9.4.5*`と`mssql-mlservices-mml-py-9.4.5*`代わりにします。

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.5*
sudo zypper install mssql-mlservices-mlm-r-9.4.5* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>例 2: 最小インストール 

R、Python、Java の拡張機能のオープン ソース R および Python に extensibility framework、microsoft openmpi のコア Revo * ライブラリが含まれています。 事前トレーニング済みモデルと machine learning の R と Python ライブラリを除外します。 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.5*
sudo zypper install mssql-mlservices-packages-r-9.4.5*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>インストール後の構成 (必須)

追加の構成は、主に、 [mssql-conf ツール](sql-server-linux-configure-mssql-conf.md)します。


1. SQL Server スタート パッド サービスを実行するために使用する mssql ユーザー アカウントを追加します。

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

2. オープン ソース R と Python のライセンス契約に同意します。 これを行ういくつかの方法はあります。 以前 SQL Server ライセンスを受け入れ、R または Python の拡張機能を追加するようになりましたすると、次のコマンドは、その条項に同意は。

  ```bash
  # Run as SUDO or root
  # Use set + EULA 
    sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
  ```

  別のワークフローは、SQL Server データベース エンジンの使用許諾契約書を許可していない場合は、セットアップによって検出されたこと、mssql mlservices パッケージおよび EULA 同意のプロンプト時に`mssql-conf setup`を実行します。 使用許諾契約書パラメーターに関する詳細については、次を参照してください。 [mssql-conf ツールで SQL Server の構成](sql-server-linux-configure-mssql-conf.md#mlservices-eula)します。

3. SQL Server スタート パッド サービスとデータベース エンジンのインスタンスを再起動します。

  ```bash
  systemctl restart mssql-launchpadd

  systemctl restart mssql-server.service
  ```

4. SQL Server Management Studio または TRANSACT-SQL を実行している別のツールでの外部スクリプト実行を有効にします。 

  ```bash
  EXEC sp_configure 'external scripts enabled', 1 
  RECONFIGURE WITH OVERRIDE 
  ```

## <a name="verify-installation"></a>インストールの確認

R ライブラリ (MicrosoftML、RevoScaleR、およびその他のユーザー) をご覧`/opt/mssql/mlservices/libraries/RServer`します。

Python ライブラリ (microsoftml および revoscalepy) をご覧`/opt/mssql/mlservices/libraries/PythonServer`します。

SQL Server のクエリ ツールを使用して、SQL Server で R の実行をテストする次の SQL コマンドを実行します。 スクリプトが実行されない場合は、サービスの再起動をお試しください`sudo systemctl restart mssql-server`します。

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
SQL Server での Python の実行をテストする次の SQL コマンドを実行します。 
 
```python
EXEC sp_execute_external_script  
@language =N'Python', 
@script=N' 
OutputDataSet = InputDataSet; 
', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```

<a name="install-all"></a>

## <a name="chained-installation"></a>チェーンのインストール

インストールして、1 つのプロシージャで R、Python、または Java のパッケージとデータベース エンジンをインストールするコマンドのパラメーターを追加して、データベース エンジンと Machine Learning サービスを構成することができます。 

次の例では、結合されたパッケージのインストールがどのように Yum パッケージ マネージャーを使用しての「テンプレート」図を示します。

```bash
sudo yum install -y mssql-sqlserver mssql-server-extensibility-java 
```

この例では、データベース エンジンをインストールし、依存関係として extensibility framework パッケージを取得する Java 言語拡張機能を追加します。 この例で使用されるパッケージのすべてについては、同じパスにあります。 R パッケージを追加する場合は、microsoft オープン r パッケージ リポジトリの登録が必要があります。

インストール後、mssql-conf ツールを使用して、インストール全体を構成し、ライセンス契約に同意することに注意してください。 オープン ソース R および Python コンポーネントの未承認の Eula が自動的に検出し、SQL Server の使用許諾契約書と共に、それらをそのまま使用するように求められます。

```bash
sudo /opt/mssql/bin/mssql-conf setup MSSQL_PID=Developer 
```

## <a name="unattended-installation"></a>無人インストール

使用して、[無人インストール](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended)データベース エンジン、mssql mlservices と Eula 用のパッケージを追加します。

セットアップや mssql-conf ツールをライセンス契約書への同意を求めることを思い出してください。 既に SQL Server データベース エンジンを構成し、その使用許諾契約書を受け入れる場合、は、オープン ソース R および Python ディストリビューション mlservices 固有の使用許諾契約書パラメーターのいずれかを使用します。

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

使用許諾契約書への同意の可能なすべての順列が記載されて[mssql-conf ツールを使った Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md#mlservices-eula)します。

## <a name="offline-installation"></a>オフライン インストール

に従って、[オフライン インストール](sql-server-linux-setup.md#offline)パッケージをインストールする方法の手順を実行します。 ダウンロード サイトを見つけて、以下のパッケージの一覧を使用して特定のパッケージをダウンロードします。

> [!Tip]
> パッケージの管理ツールのいくつか提供するのに役立つコマンドは、パッケージの依存関係を判断します。 Yum を使用して`sudo yum deplist [package]`します。 使用して、ubuntu、`sudo apt-get install --reinstall --download-only [package name]`続けて`dpkg -I [package name].deb`します。


#### <a name="download-site"></a>ダウンロード サイト

パッケージをダウンロードする[ https://packages.microsoft.com/](https://packages.microsoft.com/)します。 すべての R、Python、および Java の mlservices パッケージは、データベース エンジンのパッケージと同じ場所にします。 Mlservices パッケージの基本バージョンは 9.4. 5. です。 Micrososoft オープン r パッケージは、別のフォルダーには。

#### <a name="rhel7-paths"></a>RHEL 7/パス

|||
|--|----|
| mssql/mlservices パッケージ | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| microsoft オープン r パッケージ | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Ubuntu 16.04/パス

|||
|--|----|
| mssql/mlservices パッケージ | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| microsoft オープン r パッケージ | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>SLES 12/パス

|||
|--|----|
| mssql/mlservices パッケージ | [ https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| microsoft オープン r パッケージ | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>パッケージの一覧

どの拡張機能によってを使用するには、特定の言語のために必要なパッケージをダウンロードします。 正確なファイル名には、プラットフォームの情報が含まれますが、次のファイル名を取得するファイルを決定するための十分にする必要があります。

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-foreachiterators-3.4.4
microsoft-r-open-mkl-3.4.4
microsoft-r-open-mro-3.4.4
mssql-mlservices-packages-r-9.4.5
mssql-mlservices-mlm-r-9.4.5
mssql-mlservices-mml-r-9.4.5

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.5
mssql-mlservices-packages-py-9.4.5
mssql-mlservices-mlm-py-9.4.5
mssql-mlservices-mml-py-9.4.5 
```

## <a name="add-more-rpython-packages"></a>R および Python パッケージを追加します。 
 
その他の R と Python パッケージをインストールして、SQL Server 2019 で実行されるスクリプトで使用できます。

### <a name="r-packages"></a>R パッケージ 
 
1. R セッションを開始します。

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. 呼ばれる、R パッケージをインストール[グルー](https://mran.microsoft.com/package/glue)パッケージのインストールをテストします。

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   または、コマンドラインから、R パッケージをインストールできます。 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. R パッケージをインポート[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Python パッケージ 
 
1. という名前の Python パッケージをインストール[httpie](https://httpie.org/) pip を使用しています。 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Python パッケージをインポート[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-20"></a>CTP 2.0 の制限事項

この CTP リリースでは、次の制限があります。

+ 暗黙の認証は現在 Linux での Machine Learning Services で使用可能なデータまたはその他のリソースにアクセスする実行中の R または Python スクリプトからサーバーに接続することはできませんが、現時点で。 

+ [CREATE EXTERNAL LIBRARY](../t-sql/statements/create-external-library-transact-sql.md) (R パッケージを格納する、データベース内) でない現在 Linux で利用可能とは、Python をサポートしていません。  

### <a name="resource-governance"></a>リソース ガバナンス

Linux および Windows の間の類似性がある[リソース ガバナンス](../t-sql/statements/create-external-resource-pool-transact-sql.md)の外部リソース プールの統計情報は[sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md)が現在Linux 上のさまざまな単位です。 ユニットは、今後の CTP で揃います。
 
| 列名   | 説明 | Linux 上の値 | 
|---------------|--------------|---------------|
|peak_memory_kb | 最大リソース プールに使用されるメモリ量。 | Linux では、この統計は、値が memory.max_usage_in_bytes CGroups メモリ サブシステムからソースします。 |
|write_io_count | IOs のリソース ガバナー統計がリセットされた後に発行された書き込みの合計。 | Linux では、この統計は、書き込みの行に値が blkio.throttle.io_serviced CGroups blkio サブシステムからソースします。 | 
|read_io_count | 読み取りリソース ガバナー統計がリセットされた後に発行された Io の合計。 | Linux では、この統計情報は読み取り行の値が blkio.throttle.io_serviced は、CGroups blkio サブシステムからソースします。 | 
|total_cpu_kernel_ms | 累積的な CPU ユーザー カーネル時間 (リソース ガバナー統計がリセットされた後のミリ秒単位)。 | Linux では、この統計は、ユーザーの行に値が cpuacct.stat CGroups cpuacct サブシステムからソースします。 |  
|total_cpu_user_ms | リソース ガバナー統計がリセットされた後のミリ秒単位で累積的な CPU ユーザー時間。| Linux では、この統計は、システムの行の値に値が cpuacct.stat は、CGroups cpuacct サブシステムからソースします。 | 
|active_processes_count | 要求の時点で実行されている外部プロセスの数。| Linux では、この統計は、値が pids.current GGroups pid サブシステムからソースします。 | 

## <a name="next-steps"></a>次の手順

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行します。](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R の開発者向けチュートリアル: データベース内分析](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Python の開発者は、これらのチュートリアルに従って、SQL Server で Python を使用する方法を学ぶことができます。

+ [チュートリアル: T-SQL での Python を実行します。](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Python 開発者向けチュートリアル: データベース内分析](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)します。
