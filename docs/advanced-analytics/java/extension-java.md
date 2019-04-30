---
title: SQL Server 2019 - SQL Server の言語拡張機能での Java 言語の拡張機能
description: インストール、構成、および Linux と Windows の両方のシステムでは、SQL Server 2019 Java 言語拡張機能を検証します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: db57689227445b0f50d6ff59fbf81e1d84ecacdb
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473412"
---
# <a name="java-language-extension-in-sql-server-2019"></a>SQL Server 2019 で Java 言語の拡張機能 

Windows と Linux の両方で SQL Server 2019 preview 以降、ことを実行するカスタムの Java コードを使用、[拡張性フレームワーク](../concepts/extensibility-framework.md)データベース エンジンのインスタンスへのアドオンとして。

機能拡張フレームワークは、外部のコードを実行するためのアーキテクチャです。(SQL Server 2019 で開始)、Java [(SQL Server 2017 以降) Python](../concepts/extension-python.md)と[(SQL Server 2016 以降) R](../concepts/extension-r.md)します。 コードの実行では、コア エンジンのプロセスから分離されたが、SQL Server クエリの実行と完全に統合します。 つまり、外部ランタイム (Java) を任意の SQL Server クエリからデータをプッシュし、使用またはできる SQL Server に結果を保持します。

プログラミング言語拡張子と同様、システム ストアド プロシージャ[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)はコンパイル済みの Java コードを実行するためのインターフェイスです。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>前提条件

SQL Server 2019 プレビュー インスタンスが必要です。 以前のバージョンの Java 統合ではありません。

現在サポートされているバージョンは Java 8 です。 11、Java などの新しいバージョンでは、言語拡張子を持つ必要がありますが、現在サポートされていません。 Java ランタイム環境 (JRE) が最低限の要件が、JDK、Java コンパイラおよび開発パッケージが必要な場合に便利です。 JDK は、JDK をインストールする場合、すべて紹介するため、JRE の必要はありません。

優先、Java 8 の配布を使用することができます。 推奨される 2 つのディストリビューションを次に示します。

| Distribution | Java のバージョン | オペレーティング システム | JDK | JRE |
|-|-|-|-|-|
| [Oracle Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index.html) | 8 | Windows および Linux | はい | はい |
| [Zulu OpenJDK](https://www.azul.com/downloads/zulu/) | 8 | Windows および Linux | はい | いいえ |

Linux では、現在、 **mssql server extensibility java**パッケージがインストールされていない場合は、自動的に JRE 8 をインストールします。 インストール スクリプトは、という JRE_HOME 環境変数に JVM パスを追加する必要があります。

Windows、お勧めする既定の JDK をインストールする`/Program Files/`可能であればフォルダー。 それ以外の場合、実行可能ファイルへのアクセス許可を付与するには、追加の構成が必要です。 詳細については、次を参照してください。、 [(Windows) のアクセス許可を付与](#perms-nonwindows)このドキュメントの「します。

> [!Note]
> Java は、下位互換性があること、以前のバージョンは使えるかもしれませんが、この初期の CTP リリースのサポートされていると、テスト対象のバージョン番号は Java 8 を指定します。 

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Linux をインストールする

インストールすることができます、[データベース エンジンおよび Java 拡張機能をまとめて](../../linux/sql-server-linux-setup-machine-learning.md#install-all)、または既存のインスタンスに Java のサポートを追加します。 次の例では、既存のインストールに Java 拡張機能を追加します。  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# SUSE install commands
sudo zypper install mssql-server-extensibility-java
```

インストールするときに**mssql server extensibility java**がインストールされていない場合に、パッケージが JRE 8 に自動的にインストールされます。 JVM のパスは、という JRE_HOME 環境変数にそれも追加されます。

次の手順は、インストールを完了すると、[外部スクリプト実行を構成する](#configure-script-execution)します。

> [!Note]
> インターネットに接続されたデバイスで、パッケージの依存関係がダウンロードされ、メイン パッケージのインストールの一部としてインストールします。 詳細については、オフラインの設定などを参照してください[Linux に SQL Server Machine Learning をインストール](../../linux/sql-server-linux-setup-machine-learning.md)します。

### <a name="grant-permissions-on-linux"></a>Linux 上のアクセス許可の付与

外部ライブラリを使用している場合は、この手順を実行する必要はありません。 作業に推奨される方法は、外部ライブラリを使用しています。 Jar ファイルから外部ライブラリの作成については、次を参照してください[CREATE EXTERNAL LIBRARY。](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

外部ライブラリを使用していない場合は、jar で Java クラスを実行するアクセス許可を持つ SQL Server を指定する必要があります。

読み取りを許可し、jar ファイルへのアクセスを実行するには、次を実行**chmod** jar ファイルをコマンド。 常に SQL Server を使用する場合、クラス ファイルを jar に配置することをお勧めします。 Jar の作成については、次を参照してください。 [jar ファイルを作成する方法](#create-jar)します。

```cmd
chmod ug+rx <MyJarFile.jar>
```

Jar ファイルを読み取り/実行 mssql_satellite アクセス許可を付与する必要があります。

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

### <a name="add-the-jrehome-variable"></a>JRE_HOME 変数を追加します。

JRE_HOME は、Java のインタープリターの場所を指定するシステム環境変数です。 この手順で、Windows 上のシステム環境変数を作成します。

1. JRE ホーム パスのコピーを見つけて (たとえば、 `C:\Program Files\Zulu\zulu-8\jre\`)。

    優先の Java ディストリビューションによって JDK、JRE の場所は上記の例のパスと異なるにあります。
    JDK インストールがある場合でも多くの場合、時間がそのインストールの一環として、JRE のサブ フォルダーを取得、その場合は、jre フォルダーを指すため。
    Java 拡張機能は、パス %jre_home%\bin\server から、jvm.dll をロードしようとしています。

2. コントロール パネルで、開く**システムとセキュリティ**、オープン**システム**、 をクリック**システム プロパティの高度な**します。

3. クリックして**環境変数**します。

4. 新しいシステム変数を作成`JRE_HOME`(手順 1 で見つかった) JDK と JRE パスの値。

5. 再起動[スタート パッド](../concepts/extensibility-framework.md#launchpad)します。

    1. [[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)] を開きます。

    2. SQL Server のサービス の下には、SQL Server スタート パッドを右クリックして**再起動**します。

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jre-folder-windows-only"></a>既定ではない JRE フォルダー (Windows のみ) にアクセスを許可

JDK または JRE が program files の下にインストールしなかった場合は、次の手順を実行する必要があります。 実行、 **icacls**からコマンドを*管理者特権で*行へのアクセス許可を**SQLRUsergroup**および SQL Server サービス アカウント (で**ALL_APPLICATION_パッケージ**) JRE にアクセスするためです。 コマンドは、再帰的には、すべてのファイルと、指定したディレクトリ パスの下のフォルダーへのアクセスを許可します。

#### <a name="sqlrusergroup-permissions"></a>SQLRUserGroup のアクセス許可

名前付きインスタンスの場合、SQLRUsergroup にインスタンス名を追加します (たとえば、 `SQLRUsergroupINSTANCENAME`)。

```cmd
icacls "<PATH to JRE>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

Windows 上の program files の下の既定のフォルダーで、JDK と JRE をインストールした場合は、この手順をスキップすることができます。

#### <a name="appcontainer-permissions"></a>AppContainer アクセス許可

```cmd
icacls "PATH to JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>スクリプトの実行を構成します。

この時点では、Linux または Windows での Java コードを実行するほぼ準備が完了したら。 最後の手順としては、SQL Server Management Studio や Azure data studio、SQL CMD 外部スクリプトの実行を有効にする TRANSACT-SQL スクリプトを実行できるようにするもう 1 つのツールに切り替えます。

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>インストールの確認

インストールが動作を確認するには、作成し、実行、[サンプル アプリケーション](java-first-sample.md)先ほどインストールして JRE_HOME に追加の Java ランタイムを使用します。

## <a name="differences-in-ctp-25"></a>CTP 2.5 での相違点

Machine Learning サービス理解している場合は、拡張機能の承認および分離モデルがこのリリースで変更されました。 詳細については、次を参照してください。 [SQL Server Machine 2019 Learning サービスのインストールの違い](../install/sql-machine-learning-services-ver15.md)します。

## <a name="limitations-in-ctp-25"></a>CTP 2.5 の制限事項

* 入力と出力バッファーの値の数を超えることはできません`MAX_INT (2^31-1)`は Java で配列に割り当てることができる要素の最大数。

* 出力パラメーターで[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)は、このバージョンではサポートされていません。

* Sp_execute_external_script パラメーターを使用してストリーミング@r_rowsPerReadは、この CTP ではサポートされていません。

* Sp_execute_external_script パラメーターを使用してパーティション分割@input_data_1_partition_by_columnsは、この CTP ではサポートされていません。

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>クラス ファイルから jar ファイルを作成する方法

Jar の中に SQL Server から実行するときに、クラス ファイルを常にパッケージをお勧めします。
クラス ファイルから jar を作成するには、クラス ファイルを含むフォルダーに移動し、このコマンドを実行します。

```cmd
jar -cf <MyJar.jar> *.class
```

パスを必ず**jar.exe**はシステムの path 変数の一部です。 または、/bin JDK フォルダーの下では jar への完全パスを指定します。 `C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>次のステップ

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java サンプル](java-first-sample.md)
+ [Microsoft 拡張機能の Microsoft SQL Server 用の Java SDK](java-sdk.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)
