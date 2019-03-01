---
title: SQL Server 2019 - SQL Server Machine Learning Services での Java 言語の拡張機能
description: インストール、構成、および Linux と Windows の両方のシステムでは、SQL Server 2019 Java 言語拡張機能を検証します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a18886ea4daff3fb87853a556b67ad0562c2efd3
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017838"
---
# <a name="java-language-extension-in-sql-server-2019"></a>SQL Server 2019 で Java 言語の拡張機能 

Windows と Linux の両方で SQL Server 2019 preview 以降で実行できるカスタムの Java コード、[拡張性フレームワーク](../concepts/extensibility-framework.md)データベース エンジンのインスタンスへのアドオンとして。 

機能拡張フレームワークは、外部のコードを実行するためのアーキテクチャです。(SQL Server 2019 で開始)、Java [(SQL Server 2017 以降) Python](../concepts/extension-python.md)と[(SQL Server 2016 以降) R](../concepts/extension-r.md)します。 コードの実行では、コア エンジンのプロセスから分離されたが、SQL Server クエリの実行と完全に統合します。 つまり、外部の実行時に任意の SQL Server クエリからデータをプッシュし、使用またはできる SQL Server に結果を保持します。

プログラミング言語拡張子と同様、システム ストアド プロシージャ[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)はコンパイル済みの Java コードを実行するためのインターフェイスです。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>前提条件

SQL Server 2019 プレビュー インスタンスが必要です。 以前のバージョンの Java 統合ではありません。

Java 8 がサポートされています。 Java ランタイム環境 (JRE) が最低限の要件が、Jdk、Java コンパイラまたはパッケージを開発する必要がある場合に便利です。 JDK は、JDK をインストールする場合、すべて紹介するため、JRE の必要はありません。

優先、Java 8 の配布を使用することができます。 推奨される 2 つのディストリビューションを次に示します。

| Distribution | Java のバージョン | オペレーティング システム | JDK | JRE |
|-|-|-|-|-|
| [Oracle Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index.html) | 8 | Windows および Linux | はい | はい |
| [Zulu OpenJDK](https://www.azul.com/downloads/zulu/) | 8 | Windows および Linux | はい | いいえ |

Linux では、 **mssql server extensibility java**パッケージがインストールされていない場合は、自動的に JRE 8 をインストールします。 インストール スクリプトは、JAVA_HOME という環境変数に JVM パスを追加する必要があります。

Windows、お勧めする既定の JDK をインストールする`/Program Files/`可能であればフォルダー。 それ以外の場合、実行可能ファイルへのアクセス許可を付与するには、追加の構成が必要です。 詳細については、次を参照してください。、 [(Windows) のアクセス許可を付与](#perms-nonwindows)このドキュメントの「します。

> [!Note]
> Java は、下位互換性があること、以前のバージョンは使えるかもしれませんが、この初期の CTP リリースのサポートされていると、テスト対象のバージョン番号は Java 8 を指定します。 

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Linux をインストールします。

インストールすることができます、[データベース エンジンおよび Java 拡張機能をまとめて](../../linux/sql-server-linux-setup-machine-learning.md#install-all)、または既存のインスタンスに Java のサポートを追加します。 次の例では、既存のインストールに Java 拡張機能を追加します。  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# SUSE install commands
sudo zypper install mssql-server-extensibility-java
```

インストールするときに**mssql server extensibility java**がインストールされていない場合に、パッケージが JRE 8 に自動的にインストールされます。 JVM のパスは、JAVA_HOME という環境変数にそれも追加されます。

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

1. サポートされているバージョンの Java がインストールされていることを確認します。 詳細については、次を参照してください。、[の前提条件](#prerequisites)します。

2. [セットアップを実行](../install/sql-machine-learning-services-windows-install.md)SQL Server 2019 をインストールします。

3. 機能の選択を取得するときに選択**Machine Learning サービス (データベース)** します。 

   Java の統合は、機械学習ライブラリが付属していません、これは、機能拡張フレームワークを提供するセットアップ オプションです。 希望する場合は、R と Python を省略できます。

4. インストール ウィザードを終了し、次の 2 つのタスクを続行します。

### <a name="add-the-javahome-variable"></a>JAVA_HOME 変数を追加します。

JAVA_HOME は、Java のインタープリターの場所を指定する環境変数です。 この手順で、Windows 上のシステム環境変数を作成します。

1. JDK と JRE パスのコピーを見つけて (たとえば、 `C:\Program Files\Java\jdk1.8.0_201`)。

    優先の Java ディストリビューションによって JDK、JRE の場所は上記の例のパスと異なるにあります。

2. コントロール パネルで、開く**システムとセキュリティ**、オープン**システム**、 をクリック**システム プロパティの高度な**します。

3. クリックして**環境変数**します。

4. 新しいシステム変数を作成`JAVA_HOME`(手順 1 で見つかった) JDK と JRE パスの値。

5. 再起動[スタート パッド](../concepts/extensibility-framework.md#launchpad)します。

    1. [[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)] を開きます。

    2. SQL Server のサービス の下には、SQL Server スタート パッドを右クリックして**再起動**します。

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

## <a name="differences-in-ctp-23"></a>CTP 2.3 の相違点

Machine Learning サービス理解している場合は、拡張機能の承認および分離モデルがこのリリースで変更されました。 詳細については、次を参照してください。 [SQL Server Machine 2019 Learning サービスのインストールの違い](../install/sql-machine-learning-services-ver15.md)します。

## <a name="limitations-in-ctp-23"></a>CTP 2.3 の制限事項

* 入力と出力バッファーの値の数を超えることはできません`MAX_INT (2^31-1)`は Java で配列に割り当てることができる要素の最大数。

* 出力パラメーターで[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)は、このバージョンではサポートされていません。

* Sp_execute_external_script パラメーターを使用してストリーミング@r_rowsPerReadは、この CTP ではサポートされていません。

* Sp_execute_external_script パラメーターを使用してパーティション分割@input_data_1_partition_by_columnsは、この CTP ではサポートされていません。

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>クラス ファイルから jar ファイルを作成する方法

クラス ファイルを含むフォルダーに移動し、このコマンドを実行します。

```cmd
jar -cf <MyJar.jar> *.class
```

パスを必ず**jar.exe**はシステムの path 変数の一部です。 または、/bin JDK フォルダーの下では jar への完全パスを指定します。 `C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>次のステップ

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java サンプル](java-first-sample.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)