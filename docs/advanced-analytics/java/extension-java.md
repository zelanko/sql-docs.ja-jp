---
title: SQL Server 2019 で Java 言語の拡張機能 |Microsoft Docs
description: Java 言語の拡張機能を使用して SQL Server 2019 の Java コードを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8acb0a72435306cdec8740ffb41ff499eea61fac
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715157"
---
# <a name="java-language-extension-in-sql-server-2019"></a>SQL Server 2019 で Java 言語の拡張機能 

SQL Server 2019 以降で実行できるカスタムの Java コード、[拡張性フレームワーク](../concepts/extensibility-framework.md)データベース エンジンのインスタンスへのアドオンとして。 

機能拡張フレームワークが外部コードを実行するためのアーキテクチャ: (SQL Server 2019 で開始)、Java [(SQL Server 2017 以降) Python](../concepts/extension-python.md)、および[R (SQL Server 2016 以降)](../concepts/extension-r.md)します。 コードの実行では、コア エンジンのプロセスから分離されたが、SQL Server クエリの実行と完全に統合します。 つまり、外部の実行時に任意の SQL Server クエリからデータをプッシュし、使用またはできる SQL Server に結果を保持します。

プログラミング言語拡張子と同様、システム ストアド プロシージャ[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)はコンパイル済みの Java コードを実行するためのインターフェイスです。

## <a name="1---feature-installation"></a>1-機能のインストール

Java 言語の拡張機能をインストールするには、Windows または Linux には、SQL Server 2019 セットアップを実行します。 SQL Server 2019 データベース エンジンのインスタンスが必要です。 以前のバージョンに Java の統合を追加することはできません。

Windows では、開始、[インストール ウィザード](../install/sql-machine-learning-services-windows-install.md)します。 機能の選択 で、次のように選択します。 **Machine Learning サービス (データベース)** します。 Java の統合は、機械学習ライブラリが付属していません、これは、機能拡張フレームワークを提供するセットアップ オプションです。 希望する場合は、R と Python を省略できます。

Linux では、インストール、[データベース エンジン](https://docs.microsoft.com/sql/linux/sql-server-linux-setup)、だけでなく[機能拡張のパッケージと Java の拡張機能パッケージ](../../linux/sql-server-linux-setup-machine-learning.md)します。

次の例では、各 Linux オペレーティング システムの構文を示します。

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility
sudo zypper install mssql-server-extensibility-java
```

## <a name="2---configuration"></a>2-構成

SQL Server Management Studio または TRANSACT-SQL スクリプトを実行する別のツールを使用して、データベース エンジン インスタンスに対する外部スクリプトの実行を構成します。

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="3---bring-your-own-java"></a>3 - 独自の Java を表示します。

R や Python などの以前の言語統合から 1 つの違いは、ユーザーが制御する JVM SQL Server で使用するためです。

| Java のバージョン | オペレーティング システム |
|--------------|------------------|
| [Java 1.10](http://jdk.java.net/10/)   | Windows |
| Java 1.8   | Linux | 

Java は、下位互換性があること、以前のバージョンは使えるかもしれませんが、この初期の CTP リリースのサポートされていると、テスト対象のバージョンは、表に示すを指定します。

> [!Note]
>Java で SQL Server を実行する技術的には必要なだけ、 [Java Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) (JRE) をインストールします。 JDK が開発キット、Java コンパイラおよびその他の開発を含むパッケージに関連します。 既にしている場合、開発環境だけで、サーバー コンピューターでの Java ランタイム、JDK のインストール手順を無視し、JRE にのみインストールできます。

## <a name="jdk-on-windows"></a>JDK Windows

Windows のバージョンのダウンロード、 [Java SE Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)します。

/Program ファイルの既定の JDK をインストール/付与しなくてもすむようにする場合、フォルダーの読み取りアクセス許可を**ALL APPLICATION PACKAGES**と**SQLRUserGroup**別の場所でセキュリティ グループ. .Class または .jar ファイルを保存する場所、Java classpath フォルダーにアクセスするため、同じガイダンスが適用されます。 

> [!Note]
> 拡張機能の承認および分離モデルは、このリリースで変更されました。 詳細については、次を参照してください。 [SQL Server Machine 2019 Learning サービスのインストールの違い](../install/sql-machine-learning-services-ver15.md)します。

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>既定ではない JDK フォルダー (Windows のみ) にアクセスを許可

既定のフォルダーで、JDK と JRE をインストールした場合は、この手順をスキップすることができます。 既定のフォルダー以外のインストールでは、アクセスを許可する次の PowerShell スクリプトを実行、 **SQLRUsergroup**と JVM と Java classpath にアクセスするため (ALL_APPLICATION_PACKAGES) での SQL Server サービス アカウント。

#### <a name="sqlrusergroup-permissions"></a>SQLRUserGroup のアクセス許可

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
$Acl.SetAccessRule($Ar)
Set-Acl ""<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

#### <a name="appcontainer-permissions"></a>AppContainer アクセス許可

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
$Acl.SetAccessRule($Ar) 
Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

### <a name="add-the-jdk-path-to-javahome"></a>JAVA_HOME に JDK パスを追加します。
また、"JAVA_HOME"を名前で、システム環境変数を JDK と JRE のインストール パス (たとえば、"C:\Program Files\Java\jdk-10.0.2") を追加する必要があります。 

システム変数を作成するには、コントロール パネルを使用 > システムとセキュリティ > にアクセスするシステム**システム プロパティの高度な**します。 クリックして**環境変数**し、JAVA_HOME を新しいシステム変数を作成します。

![Java ホームの環境変数を](../media/java/env-variable-java-home.png "Java 用のセットアップ")

## <a name="jdk-on-linux"></a>Linux 上の JDK

Linux では、mssql server extensibility java パッケージがインストールされていない場合は、JRE 1.8 が自動的にインストールされます。 JVM のパスは、JAVA_HOME という環境変数にそれも追加されます。

## <a name="limitations-in-ctp-20"></a>CTP 2.0 の制限事項

* 入力と出力バッファーの値の数を超えることはできません`MAX_INT (2^31-1)`は Java で配列に割り当てることができる要素の最大数。

* Sp_execute_external_script で出力パラメーターは、このバージョンではサポートされません。

* LOB データ型がこのバージョンでは、入力と出力のデータ セットはサポートされません。 参照してください[Java および SQL Server データ型](java-sql-datatypes.md)詳細についてはこの CTP ではデータの種類がサポートされています。

* Sp_execute_external_script パラメーターを使用してストリーミング@r_rowsPerReadは、この CTP ではサポートされていません。

* Sp_execute_external_script パラメーターを使用してパーティション分割@input_data_1_partition_by_columnsは、この CTP ではサポートされていません。

## <a name="next-steps"></a>次の手順

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java サンプル](java-first-sample.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)