---
title: "高度なデータ型を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b39461d3-48d6-4048-8300-1a886c00756d
caps.latest.revision: 58
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b74ed587d91e351f91db2e3ef2a45c41edf37918
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-advanced-data-types"></a>高度なデータ型の使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] JDBC データ型の詳細を使用して変換する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型には、プログラミング言語を Java で認識できる形式にします。  
  
## <a name="remarks"></a>解説  
 次の表は、既定のマッピング、高度な[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]JDBC、および Java プログラミング言語のデータ型。  
  
|SQL Server 型|JDBC 型 (java.sql.Types)|Java 言語型|  
|----------------------|-----------------------------------|-------------------------|  
|varbinary(max)<br /><br /> image|LONGVARBINARY|byte[]\(既定)、Blob、InputStream、文字列|  
|text<br /><br /> varchar(max)|LONGVARCHAR|String (既定)、Clob、InputStream|  
|ntext<br /><br /> nvarchar(max)|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String (既定)、Clob、NClob (Java SE 6.0)|  
|xml|LONGVARCHAR<br /><br /> SQLXML (Java SE 6.0)|String (既定)、InputStream、Clob、byte[]、Blob、SQLXML (Java SE 6.0)|  
|Udt<sup>1</sup>|VARBINARY|String (既定)、byte[]、InputStream|  
  
 <sup>1</sup> 、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]バイナリ データとしての CLR Udt の送受信をサポートしていますが、CLR メタデータの操作をサポートしていません。  
  
 以下のセクションでは、JDBC ドライバーと高度なデータ型の使用方法の例を示します。  
  
## <a name="blob-and-clob-and-nclob-data-types"></a>BLOB、CLOB、および NCLOB データ型  
 JDBC ドライバーは、java.sql.Blob、java.sql.Clob、および java.sql.NClob インターフェイスのすべてのメソッドを実装しています。  
  
> [!NOTE]  
>  CLOB 値で使用できる[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)](またはそれ以降) の大きな値データ型。 具体的には、CLOB 型はで使用できる、 **varchar (max)**と**nvarchar (max)**データ型の場合は、BLOB 型で使用できます**varbinary (max)**と**イメージ**データ型、および NCLOB 型で使える**ntext**と**nvarchar (max)**です。  
  
## <a name="large-value-data-types"></a>大きな値のデータ型  
 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、大きな値のデータ型の特別な処理が必要です。 大きな値をとるデータ型とは、最大行サイズが 8 KB を超えるデータ型のことです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]max 指定子が導入されています**varchar**、 **nvarchar**、および**varbinary** 2 と同じ大きさの値を格納を許可するデータ型 ^31 バイトです。 テーブルの列と[!INCLUDE[tsql](../../includes/tsql_md.md)]変数を指定できます**varchar (max)**、 **nvarchar (max)**、または**varbinary (max)**データ型。  
  
 大きな値の型を操作する主要なシナリオには、データベースからの取得とデータベースへの追加があります。 以下のセクションでは、これらのタスクを実行するためのさまざまな方法について説明します。  
  
### <a name="retrieving-large-value-types-from-a-database"></a>データベースからの大きな値の型の取得  
 非バイナリの大きな値データ型を取得する場合: など、 **varchar (max)**データ型 — をデータベースから 1 つの方法がデータを文字ストリームとして読み取ることができます。 次の例で、 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスは、データベースからデータを取得し、結果セットとして返すに使用します。 続いて、 [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスは、結果セットから大きな値データの読み取りに使用します。  
  
```  
ResultSet rs = stmt.executeQuery("SELECT TOP 1 * FROM Test1");  
rs.next();  
Reader reader = rs.getCharacterStream(2);  
```  
  
> [!NOTE]  
>  これと同じアプローチにも使用できます、**テキスト**、 **ntext**、および**nvarchar (max)**データ型。  
  
 バイナリの大きな値データ型を取得する場合: など、 **varbinary (max)**データ型: データベースからは、いくつかのアプローチを行うことができます。 最も効率的に行うには、次のようにバイナリ ストリームとしてデータを読み取ります。  
  
```  
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
InputStream is = rs.getBinaryStream(2);  
```  
  
 使用することも、 [getBytes](../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)メソッドを次のように、バイト配列としてデータを読み取る。  
  
```  
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
byte [] b = rs.getBytes(2);  
```  
  
> [!NOTE]  
>  BLOB としてデータを読み取ることもできます。 ただし、前述の 2 つの方法より効率が下がります。  
  
### <a name="adding-large-value-types-to-a-database"></a>データベースへの大きな値の型の追加  
 JDBC ドライバーを使用した大きいデータのアップロードは、メモリ内に収まる場合は、適切に行うことができます。メモリ内に収まらない場合は、ストリームを使用するのが主要なオプションです。 ただし、最も効率的に大きいデータをアップロードするためには、ストリーム インターフェイスを使用します。  
  
 次に示すように、文字列やバイトを使用する方法もあります。  
  
```  
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (c1_id, c2_vcmax) VALUES (?, ?)");  
pstmt.setInt(1, 1);  
pstmt.setString(2, htmlStr);  
pstmt.executeUpdate();  
```  
  
> [!NOTE]  
>  この方法に格納されている値に対しても使用できます**テキスト**、 **ntext**、および**nvarchar (max)**列です。  
  
 全体のバイナリ イメージ ファイルをアップロードする必要があり、サーバーにイメージ ライブラリをした場合、 **varbinary (max)**次のように、直接ストリームを使用する列、JDBC ドライバーで最も効率的な方法は。  
  
```  
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (Col1, Col2) VALUES(?,?)");  
File inputFile = new File("CLOBFile20mb.jpg");  
FileInputStream inStream = new FileInputStream(inputFile);  
int id = 1;  
pstmt.setInt(1,id);  
pstmt.setBinaryStream(2, inStream);  
pstmt.executeUpdate();  
inStream.close();  
```  
  
> [!NOTE]  
>  CLOB または BLOB メソッドの使用は、大きいデータをアップロードする際に効率的ではありません。  
  
### <a name="modifying-large-value-types-in-a-database"></a>データベースの大きな値の型の変更  
 ほとんどの場合、更新またはデータベースの大きい値を変更するための推奨される方法を使用したパラメーターを渡す、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラス使用して[!INCLUDE[tsql](../../includes/tsql_md.md)]更新プログラム、書き込み、および SUBSTRING などのコマンド。  
  
 アーカイブされた HTML ファイルなど、大きなテキスト ファイルに含まれる単語のインスタンスを置換する必要がある場合は、次のように、Clob オブジェクトを使用できます。  
  
```  
String SQL = "SELECT * FROM test1;";  
Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);  
ResultSet rs = stmt.executeQuery(SQL);  
rs.next();  
  
Clob clob = rs.getClob(2);  
long pos = clob.position("dog", 1);  
clob.setString(pos, "cat");  
rs.updateClob(2, clob);  
rs.updateRow();  
```  
  
 また、すべての作業をサーバー上で行い、準備された UPDATE ステートメントにパラメーターを渡すこともできます。  
  
 大きな値の型の詳細については、SQL Server オンライン ブックの「大きな値をとるデータ型の使用」を参照してください。  
  
## <a name="xml-data-type"></a>XML データ型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]提供、 **xml**データ型を XML ドキュメントを格納して、フラグメント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 **Xml**データ型は、組み込みのデータ型で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]などの他の組み込み型のようないくつかの方法であると**int**と**varchar**です。 他の組み込み型にも使用できるように、 **xml**型データ テーブルを作成するときに列の型として以外の場合は、変数の型、パラメーターの型、または関数の戻り値型であるとして、またはで[!INCLUDE[tsql](../../includes/tsql_md.md)]CAST や CONVERT 関数。  
  
 JDBC ドライバーで、 **xml**データ型は、文字列、バイト配列、ストリーム、CLOB、BLOB、または SQLXML オブジェクトとしてマップすることができます。 文字列が既定値です。 JDBC Driver Version 2.0 以降では、SQLXML インターフェイスを導入した JDBC 4.0 API がサポートされます。 SQLXML インターフェイスは、対話し、XML データを操作するメソッドを定義します。 **SQLXML**データ型にマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml**データ型。 リレーショナル データベースに XML データを読み書きする方法の詳細についての**SQLXML** Java データ型を参照してください[XML データをサポートする](../../connect/jdbc/supporting-xml-data.md)です。  
  
 実装、 **xml** JDBC ドライバーでのデータ型は、次のサポートを提供します。  
  
-   最も一般的なプログラミング シナリオに対し、標準 Java UTF-16 文字列として XML にアクセスできます。  
  
-   UTF-8 および他の 8 ビットでエンコードされた XML を入力できます。  
  
-   他の XML プロセッサやディスク ファイルとのやり取りのために UTF-16 でエンコードされている場合、先頭に BOM の付いた byte 配列として XML にアクセスできます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]UTF 16 でエンコードされた XML に対して先頭の BOM が必要です。 XML パラメーターの値がバイト配列として指定されている場合は、アプリケーションでこれを提供する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]常に utf-16 BOM なしを使用した文字列または埋め込みエンコード宣言としては、XML 値を出力します。 XML 値が byte[]、BinaryStream、または Blob として取得される場合、UTF-16 BOM が値の前に付いています。  
  
 詳細については、 **xml**データ型を参照してください"xml データ型"[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="user-defined-data-type"></a>ユーザー定義データ型  
 ユーザー定義型 (Udt) の導入[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]オブジェクトやカスタム データ構造を格納することにより、SQL 型システムを拡張し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 UDT は複数のデータ型を保持でき、動作を含むことができるので、1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] システム データ型だけで構成される従来の別名データ型とは異なります。 UDT は、検証可能なコードを生成する、Microsoft .NET 共通言語ランタイム (CLR) によってサポートされている任意の言語を使用して定義されます。 その言語には、Microsoft Visual C# および Visual Basic .NET が含まれます。 データは .NET Framework ベースのクラスまたは構造体のフィールドとプロパティとして公開され、動作はクラスまたは構造体のメソッドによって定義されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、UDT の変数として、テーブルの列の定義として使用できる、[!INCLUDE[tsql](../../includes/tsql_md.md)]バッチ、またはの引数として、[!INCLUDE[tsql](../../includes/tsql_md.md)]関数またはストアド プロシージャです。  
  
 ユーザー定義データ型の詳細についてを参照してください"を使用してユーザー定義型のインスタンスを変更する"[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型をについてください。](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

