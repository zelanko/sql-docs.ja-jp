---
title: SQL Server 2019 - SQL Server Machine Learning Services での Java 言語の拡張機能
description: インストール、構成、および Linux と Windows の両方のシステムでは、SQL Server 2019 Java 言語拡張機能を検証します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/07/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a258573ff7506f2533c2f91edb5751cfd1121dc8
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431716"
---
# <a name="java-language-extension-in-sql-server-2019"></a>SQL Server 2019 で Java 言語の拡張機能 

Windows と Linux の両方で SQL Server 2019 preview 以降で実行できるカスタムの Java コード、[拡張性フレームワーク](../concepts/extensibility-framework.md)データベース エンジンのインスタンスへのアドオンとして。 

機能拡張フレームワークは、外部のコードを実行するためのアーキテクチャです。(SQL Server 2019 で開始)、Java [(SQL Server 2017 以降) Python](../concepts/extension-python.md)と[(SQL Server 2016 以降) R](../concepts/extension-r.md)します。 コードの実行では、コア エンジンのプロセスから分離されたが、SQL Server クエリの実行と完全に統合します。 つまり、外部の実行時に任意の SQL Server クエリからデータをプッシュし、使用またはできる SQL Server に結果を保持します。

プログラミング言語拡張子と同様、システム ストアド プロシージャ[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)はコンパイル済みの Java コードを実行するためのインターフェイスです。

## <a name="prerequisites"></a>前提条件

SQL Server 2019 プレビュー インスタンスが必要です。 以前のバージョンの Java 統合ではありません。 

Java バージョンの要件は、Windows および Linux 全体では異なります。 Java ランタイム環境 (JRE) が最低限の要件が、Jdk、Java コンパイラまたはパッケージを開発する必要がある場合に便利です。 JDK は、JDK をインストールする場合、すべて紹介するため、JRE の必要はありません。

| オペレーティング システム | Java のバージョン | JRE のダウンロード | JDK ダウンロード |
|------------------|--------------|--------------|--------------|
| Windows          | 1.10         | [JRE 10](https://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) | [JDK 10](https://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)  |
| Linux            | 1.8          |  [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) | [JDK 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  |  

Linux では、 **mssql server extensibility java**がインストールされていない場合にパッケージが JRE 1.8 に自動的にインストールされます。 インストール スクリプトは、JAVA_HOME という環境変数に JVM パスを追加する必要があります。

Windows をお勧め/Program ファイルの既定の JDK をインストール/フォルダーを可能な場合。 それ以外の場合、実行可能ファイルへのアクセス許可を付与するには、追加の構成が必要です。 詳細については、次を参照してください。、 [(Windows) のアクセス許可を付与](#perms-nonwindows)このドキュメントの「します。

> [!Note]
> Java は、下位互換性があること、以前のバージョンは使えるかもしれませんが、この初期の CTP リリースのサポートされていると、テスト対象のバージョンは、表に示すを指定します。

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Linux をインストールします。

インストールすることができます、[データベース エンジンおよび Java 拡張機能をまとめて](../../linux/sql-server-linux-setup-machine-learning.md#install-all)、または既存のインスタンスに Java のサポートを追加します。 次の例では、既存のインストールに Java 拡張機能を追加します。  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility-java
```

インストールするときに**mssql server extensibility java**がインストールされていない場合に、パッケージが JRE 1.8 に自動的にインストールされます。 JVM のパスは、JAVA_HOME という環境変数にそれも追加されます。

次の手順は、インストールを完了すると、[外部スクリプト実行を構成する](#configure-script-execution)します。

> [!Note]
> インターネットに接続されたデバイスで、パッケージの依存関係がダウンロードされ、メイン パッケージのインストールの一部としてインストールします。 詳細については、オフラインの設定などを参照してください[Linux に SQL Server Machine Learning をインストール](../../linux/sql-server-linux-setup-machine-learning.md)します。

### <a name="grant-permissions-on-linux"></a>Linux 上のアクセス許可の付与

Java クラスを実行するアクセス許可を持つ SQL Server を指定するには、アクセス許可を設定する必要があります。

読み取りを許可し、jar ファイルまたはクラス ファイルへのアクセスを実行するには、次を実行**chmod**クラスや jar ファイルの各コマンド。 SQL Server を使用するときに、jar のクラス ファイルを配置することをお勧めします。 Jar の作成については、次を参照してください。 [jar ファイルを作成する方法](#create-jar)します。

```cmd
chmod ug+rx <MyJarFile.jar>
```
ディレクトリまたは jar ファイルを読み取り/実行 mssql_satellite アクセス許可を付与する必要があります。

* SQL Server からのクラス ファイルを呼び出す場合 mssql_satellite は必要がある読み取り/実行アクセス許可で*すべて*直接の親までのルートから、フォルダー階層内のディレクトリ。

* SQL Server から jar ファイルを呼び出す場合は、jar ファイル自体で、コマンドを実行するで十分です。

```cmd
chown mssql_satellite:mssql_satellite <directory>
```

```cmd
chown mssql_satellite:mssql_satellite <MyJarFile.jar>
```

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Windows へのインストール

1. [セットアップを実行](../install/sql-machine-learning-services-windows-install.md)SQL Server 2019 をインストールします。

2. 機能の選択を取得するときに選択**Machine Learning サービス (データベース)** します。 

   Java の統合は、機械学習ライブラリが付属していません、これは、機能拡張フレームワークを提供するセットアップ オプションです。 希望する場合は、R と Python を省略できます。

3. インストール ウィザードを終了し、次の 2 つのタスクを続行します。

### <a name="add-the-javahome-variable"></a>JAVA_HOME 変数を追加します。

JAVA_HOME は、Java のインタープリターの場所を指定する環境変数です。 この手順で、Windows 上のシステム環境変数を作成します。

1. 検索し、JDK と JRE のインストール パス (たとえば、C:\Program Files\Java\jdk-10.0.2) をコピーします。

  CTP 2.0 で基本 jdk フォルダーに JAVA_HOME を設定だけが、Java 1.10 します。 

  Java 1.8 の場合、JDK (たとえば、"C:\Program Files\Java\jdk1.8.0_181\bin\server"での Windows で jvm.dll に到達するパスを拡張します。 または、JRE のベース フォルダーをポイントすることができます。"C:\Program Files\Java\jre1.8.0_181"。

2. コントロール パネルで、開く**システムとセキュリティ**、オープン**システム**、 をクリック**システム プロパティの高度な**します。

3. クリックして**環境変数**します。

4. JAVA_HOME の新しいシステム変数を作成します。

   ![Java ホームの環境変数を](../media/java/env-variable-java-home.png "Java 用のセットアップ")

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>既定ではない JDK フォルダー (Windows のみ) にアクセスを許可

既定のフォルダーで、JDK と JRE をインストールした場合は、この手順をスキップすることができます。 

既定のフォルダー以外のインストールでは、実行、 **icacls**からコマンドを*管理者特権で*行へのアクセス許可を**SQLRUsergroup**と ( SQLServerサービスアカウント**ALL_APPLICATION_PACKAGES**) JVM や Java classpath にアクセスします。 コマンドは、再帰的には、すべてのファイルと、指定したディレクトリ パスの下のフォルダーへのアクセスを許可します。

#### <a name="sqlrusergroup-permissions"></a>SQLRUserGroup のアクセス許可

名前付きインスタンスの場合、SQLRUsergroup にインスタンス名を追加します (たとえば、 `SQLRUsergroupINSTANCENAME`)。

```cmd
icacls "<PATH TO CLASS or JAR FILES>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

#### <a name="appcontainer-permissions"></a>AppContainer アクセス許可

```cmd
icacls "PATH to JDK/JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

### <a name="add-the-jre-path-to-javahome"></a>JAVA_HOME を JRE のパスを追加します。
JAVA_HOME のシステム環境変数に JRE へのパスを追加する必要があります。 インストールされている JRE のみの場合は、JRE フォルダーのパスを行うことができます。 ただし、JDK をインストールした場合はこのような JDK、JRE フォルダーに、jvm の完全パスを指定する必要があります。"C:\Program Files\Java\jdk1.8.0_191\jre\bin\server"。

システム変数を作成するには、コントロール パネルを使用 > システムとセキュリティ > にアクセスするシステム**システム プロパティの高度な**します。 クリックして**環境変数**し、JAVA_HOME を新しいシステム変数を作成します。

![Java ホームの環境変数を](../media/java/env-variable-java-home.png "Java 用のセットアップ")

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>スクリプトの実行を構成します。

この時点では、Linux または Windows での Java コードを実行するほぼ準備が完了したら。 最後の手順としては、SQL Server Management Studio または外部スクリプトの実行を有効にする TRANSACT-SQL スクリプトを実行している他のツールに切り替えます。

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>インストールの確認

インストールが動作を確認するには、作成して実行を[サンプル アプリケーション](java-first-sample.md)JDK をインストールした、ファイルを配置する前に構成した classpath を使用します。

## <a name="differences-in-ctp-20"></a>CTP 2.0 での相違点

Machine Learning サービス理解している場合は、拡張機能の承認および分離モデルがこのリリースで変更されました。 詳細については、次を参照してください。 [SQL Server Machine 2019 Learning サービスのインストールの違い](../install/sql-machine-learning-services-ver15.md)します。

## <a name="limitations-in-ctp-20"></a>CTP 2.0 の制限事項

* 入力と出力バッファーの値の数を超えることはできません`MAX_INT (2^31-1)`は Java で配列に割り当てることができる要素の最大数。

* 出力パラメーターで[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)は、このバージョンではサポートされていません。

* LOB データ型がこのバージョンでは、入力と出力のデータ セットはサポートされません。 参照してください[Java および SQL Server データ型](java-sql-datatypes.md)詳細についてはこの CTP ではデータの種類がサポートされています。

* Sp_execute_external_script パラメーターを使用してストリーミング@r_rowsPerReadは、この CTP ではサポートされていません。

* Sp_execute_external_script パラメーターを使用してパーティション分割@input_data_1_partition_by_columnsは、この CTP ではサポートされていません。

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>クラス ファイルから jar ファイルを作成する方法

クラス ファイルを含むフォルダーに移動し、このコマンドを実行します。

```cmd
jar -cf <MyJar.jar> *.class
```

パスを必ず**jar.exe**はシステムの path 変数の一部です。 または、/bin JDK フォルダーの下では jar への完全パスを指定します。 `C:\Users\MyUser\Desktop\jdk-10.0.2\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>次の手順

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java サンプル](java-first-sample.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)