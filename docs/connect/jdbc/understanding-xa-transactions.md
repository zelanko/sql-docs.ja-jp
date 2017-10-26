---
title: "XA トランザクションについて |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 574e326f-0520-4003-bdf1-62d92c3db457
caps.latest.revision: 80
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b1ceff7c271688fcabf3206c4ba1fe0147e2afe4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-xa-transactions"></a>XA トランザクションについて」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Java Platform, Enterprise Edition/JDBC 2.0 の省略可能な分散トランザクションのサポートを提供します。 取得される JDBC 接続、 [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)クラスは、Java Platform, Enterprise Edition (Java EE) アプリケーション サーバーなどの環境の処理の標準分散トランザクションに参加できます。  
  
> [!WARNING]  
>  Microsoft JDBC Driver 4.2 (以降) SQL に準備されていないトランザクションの自動でロールバックの既存の機能の新しいタイムアウト オプションが含まれています。 参照してください[準備されていないトランザクションが自動的にロールバックのサーバー側のタイムアウト設定を構成する](../../connect/jdbc/understanding-xa-transactions.md#BKMK_ServerSide)詳細については、このトピックで後述します。  
  
## <a name="remarks"></a>解説  
 分散トランザクションを実装するためのクラスは、次のとおりです。  
  
|クラス|実装|Description|  
|-----------|----------------|-----------------|  
|com.microsoft.sqlserver.jdbc.SQLServerXADataSource|javax.sql.XADataSource|分散された接続用のクラス ファクトリです。|  
|com.microsoft.sqlserver.jdbc.SQLServerXAResource|javax.transaction.xa.XAResource|トランザクション マネージャー用のリソース アダプターです。|  
  
> [!NOTE]  
>  XA 分散トランザクション接続の既定の分離レベルは Read Committed です。  
  
## <a name="guidelines-and-limitations-when-using-xa-transactions"></a>XA トランザクションを使用する場合のガイドラインと制限  
 密に結合されたトランザクションには別途、次のガイドラインが適用されます。  
  
-   XA トランザクションを Microsoft 分散トランザクション コーディネーター (MS DTC) と組み合わせて使用すると、現在のバージョンの MS DTC では、密に結合された XA ブランチ動作がサポートされない場合があります。 たとえば、MS DTC では、XA ブランチ トランザクション ID (XID) と MS DTC トランザクション ID とが一対一でマップされ、疎結合の XA ブランチによって実行される作業どうしが分離されます。  
  
     修正プログラムを適用[MSDTC と密に結合されたトランザクション](http://support.microsoft.com/kb/938653)同じグローバル トランザクション ID (GTRID) を持つ複数の XA のブランチを密に結合された XA ブランチが 1 つの MS DTC トランザクション ID にマップされて、サポートを有効 このサポートにより、変更を表示するいずれかに別のリソース マネージャーなどの複数の密に結合された XA ブランチ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   A [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)フラグにより、密に結合された XA トランザクションを別の XA ブランチ トランザクション Id (BQUAL) が、同じグローバル トランザクション ID (GTRID) および形式 ID (FormatID) を使用するアプリケーション。 その機能を使用するために設定する必要があります、 [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) XAResource.start メソッドのパラメーターのフラグ。  
  
    ```  
    xaRes.start(xid, SQLServerXAResource.SSTRANSTIGHTLYCPLD);  
    ```  
  
## <a name="configuration-instructions"></a>構成の手順  
 以下の手順は、分散トランザクションを処理するために XA データ ソースを Microsoft 分散トランザクション コーディネーター (MS DTC) と組み合わせて使用する場合に必要になります。  
  
> [!NOTE]  
>  JDBC 分散トランザクション コンポーネントは、JDBC Driver のインストール先の xa ディレクトリに含まれます。 これらのコンポーネントには、xa_install.sql および sqljdbc_xa.dll のファイルが含まれます。  
  
### <a name="running-the-ms-dtc-service"></a>MS DTC サービスを実行する  
 MS DTC サービスをマークする必要があります**自動**ときに実行されているかどうかを確認する Service Manager で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]サービスを開始します。 XA トランザクションで使用するために MS DTC を有効にするには、次の手順を実行する必要があります。  
  
 Windows Vista 以降の場合:   
  
1.  をクリックして、**開始** ボタンを入力**dcomcnfg** Start で**検索**ボックスし、enter キーを押してを開くには**コンポーネント サービス**です。 %Windir%\system32\comexp.msc」と入力することも、 **StartSearch**ボックスを開くには**コンポーネント サービス**です。  
  
2.  [コンポーネント サービス]、[コンピューター]、[マイ コンピューター]、[分散トランザクション コーディネーター] の順に展開します。  
  
3.  右クリック**ローカル DTC**し、**プロパティ**です。  
  
4.  クリックして、**セキュリティ**タブで、**ローカル DTC のプロパティ** ダイアログ ボックス。  
  
5.  選択、 **XA トランザクションを有効にする**チェック ボックスをクリックして**OK**です。 これにより、MS DTC サービスが再開されます。  
  
6.  をクリックして**OK**を閉じます、**プロパティ** ダイアログ ボックスを閉じて、**コンポーネント サービス**です。  
  
7.  停止してから再起動[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]MS DTC の変更が反映されるかどうかを確認します。  
  
### <a name="configuring-the-jdbc-distributed-transaction-components"></a>JDBC 分散トランザクション コンポーネントを構成する  
 次の手順を実行して、JDBC Driver 分散トランザクション コンポーネントを構成できます。  
  
1.  JDBC driver のインストール ディレクトリから新しい sqljdbc_xa.dll の Binn ディレクトリにコピーすべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に参加するコンピューターに分散トランザクションです。  
  
    > [!NOTE]  
    >  32 ビットので XA トランザクションを使用しているかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、x86 の sqljdbc_xa.dll ファイルを使用する場合でも、フォルダー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を x64 がインストールされているプロセッサ。 64 ビットので XA トランザクションを使用しているかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]x64 プロセッサでは、x64 の sqljdbc_xa.dll ファイルを使用してフォルダーです。  
  
2.  Xa_install.sql データベース スクリプトを実行すべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンスに参加する分散トランザクションです。 このスクリプトによって、sqljdbc_xa.dll から呼び出される拡張ストアド プロシージャがインストールされます。 これらの拡張ストアド プロシージャの実装の分散トランザクションと XA サポートを[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]です。 管理者としてこのスクリプトを実行する必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンス。  
  
3.  JDBC Driver を使用して分散トランザクションに参加する、特定のユーザーに対してアクセス許可を与えるには、そのユーザーを SqlJDBCXAUser ロールに追加します。  
  
 それぞれに対して構成できる sqljdbc_xa.dll アセンブリの 1 つだけバージョン[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]一度にインスタンス。 アプリケーションが同じへの接続に別のバージョンの JDBC ドライバーを使用する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]XA 接続を使用してインスタンス。 その場合は、最新の JDBC driver に付属する sqljdbc_xa.dll をインストールする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンス。  
  
 Sqljdbc_xa.dll のバージョンが現在インストールされていることを確認する方法を次の 3 つが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンス。  
  
1.  LOG ディレクトリを開く[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に参加するコンピューターに分散トランザクションです。 選択し、開く、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "ERRORLOG"ファイル。 "ERRORLOG" ファイルで、"'SQLJDBC_XA.dll' バージョンを使用して..." というフレーズを探します。  
  
2.  Binn ディレクトリを開き[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に参加するコンピューターに分散トランザクションです。Sqljdbc_xa.dll アセンブリを選択します。  
  
    -   Windows Vista 以降の場合: sqljdbc_xa.dll を右クリックし、[プロパティ] を選択します。 をクリックして、**詳細**タブです。**ファイル バージョン**フィールドに現在インストールされている sqljdbc_xa.dll のバージョンを示しています、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンス。  
  
3.  次のセクションのコード例に従ってログ機能を設定します。 出力ログ ファイルで、"Server XA DLL バージョン:..." というフレーズを探します。  
  
###  <a name="BKMK_ServerSide"></a>準備されていないトランザクションが自動的にロールバックのサーバー側のタイムアウト設定を構成します。  
  
> [!WARNING]  
>  サーバー側は、このオプションは、新しい Microsoft JDBC Driver 4.2 (以降) for SQL Server。 このように動作を更新するには、サーバー上の sqljdbc_xa.dll が更新されていることをご確認ください。 クライアント側のタイムアウトを設定する方法の詳細については、次を参照してください。 [XAResource.setTransactionTimeout()](http://docs.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html)です。  
  
 分散トランザクションのタイムアウトの動作を制御する 2 つのレジストリ設定 (DWORD 値) があります。  
  
-   **XADefaultTimeout** (単位は秒): ユーザーが何らかのタイムアウトを指定しないときに使用される既定のタイムアウト値。 既定値は 0 です。  
  
-   **XAMaxTimeout** (単位は秒): ユーザーが設定可能なタイムアウトの最大値。 既定値は 0 です。  
  
 これらの設定は SQL Server インスタンス固有で、次のレジストリ キーの下に作成する必要があります。  
  
 Hkey_local_machine \software\microsoft\microsoft SQL server \mssql\<**バージョン**>.\<*instance_name*> \XATimeout  
  
> [!NOTE]  
>  32 ビットの SQL server が 64 ビット コンピューターで実行されている、次のキーの下で、レジストリ設定を作成する必要があります: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Microsoft SQL server \mssql\<バージョン >. < instance_name > \XATimeout  
  
 各トランザクションが開始されるとタイムアウト値が設定され、タイムアウトになるとトランザクションは SQL Server からロールバックされます。 タイムアウトは、これらのレジストリ設定と、ユーザーによる XAResource.setTransactionTimeout() での指定によって決定されます。 これらのタイムアウト値の解釈のいくつかの例を以下に示します。  
  
-   XADefaultTimeout = 0、XAMaxTimeout = 0  
  
     既定のタイムアウトは使用されず、クライアントにタイムアウトの最大値は適用されないことを意味します。 この場合、クライアントが XAResource.setTransactionTimeout を使用してタイムアウトを設定する場合にのみ、トランザクションにタイムアウトが適用されます。  
  
-   XADefaultTimeout = 60、XAMaxTimeout = 0  
  
     クライアントがタイムアウトを指定しない場合、すべてのトランザクションに 60 秒のタイムアウトが適用されることを意味します。 クライアントがタイムアウトを指定する場合、そのタイムアウト値が使用されます。 タイムアウトの最大値は適用されません。  
  
-   XADefaultTimeout = 30、XAMaxTimeout = 60  
  
     クライアントがタイムアウトを指定しない場合、すべてのトランザクションに 30 秒のタイムアウトが適用されることを意味します。 クライアントが何らかのタイムアウトを指定する場合、60 秒 (最大値) 以内であれば、クライアントのタイムアウト値が使用されます。  
  
-   XADefaultTimeout = 0、XAMaxTimeout = 30  
  
     クライアントがタイムアウトを指定しない場合、すべてのトランザクションに 30 秒のタイムアウト (最大値) が適用されることを意味します。 クライアントが何らかのタイムアウトを指定する場合、30 秒 (最大値) 以内であれば、クライアントのタイムアウト値が使用されます。  
  
### <a name="upgrading-sqljdbcxadll"></a>sqljdbc_xa.dll のアップグレード  
 新しいバージョンの JDBC Driver をインストールする場合は、新しいバージョンに含まれる sqljdbc_xa.dll を使用して、サーバー上の sqljdbc_xa.dll もアップグレードする必要があります。  
  
> [!IMPORTANT]  
>  sqljdbc_xa.dll のアップグレードは、メンテナンス ウィンドウ内で行うか、進行中の MS DTC トランザクションがないときに行ってください。  
  
1.  アンロード sqljdbc_xa.dll を使用して、[!INCLUDE[tsql](../../includes/tsql_md.md)]コマンド**DBCC sqljdbc_xa (無料)**です。  
  
2.  JDBC driver のインストール ディレクトリから新しい sqljdbc_xa.dll の Binn ディレクトリにコピーすべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に参加するコンピューターに分散トランザクションです。  
  
     sqljdbc_xa.dll 内の拡張プロシージャが呼び出されると、新しい DLL が読み込まれます。 再起動する必要はありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]新しい定義を読み込めません。  
  
### <a name="configuring-the-user-defined-roles"></a>ユーザー定義ロールを構成する  
 JDBC Driver を使用して分散トランザクションに参加する、特定のユーザーに対してアクセス許可を与えるには、そのユーザーを SqlJDBCXAUser ロールに追加します。 たとえば、次を使用して[!INCLUDE[tsql](../../includes/tsql_md.md)]'shelby' ('shelby' という名前 SQL 標準的なログイン ユーザー) をという名前のユーザーを SqlJDBCXAUser ロールに追加するコード。  
  
```  
USE master  
GO  
EXEC sp_grantdbaccess 'shelby', 'shelby'  
GO  
EXEC sp_addrolemember [SqlJDBCXAUser], 'shelby'  
```  
  
 SQL ユーザー定義ロールは、データベースごとに定義されます。 セキュリティ上の目的で独自のロールを作成するには、各データベースでロールを定義し、データベースごとにユーザーを追加する必要があります。 SqlJDBCXAUser ロールは、マスターに存在する SQL JDBC 拡張ストアド プロシージャへのアクセス許可に使用されるため、master データベースで厳密に定義されています。 まず、個々のユーザーのマスターへのアクセスを許可し、次に、master データベースにログオンしてから、SqlJDBCXAUser ロールへのアクセスを許可する必要があります。  
  
## <a name="example"></a>例  
  
```  
import java.net.Inet4Address;  
import java.sql.*;  
import java.util.Random;  
import javax.transaction.xa.*;  
import javax.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class testXA {  
  
   public static void main(String[] args) throws Exception {  
  
      // Create variables for the connection string.  
      String prefix = "jdbc:sqlserver://";  
      String serverName = "localhost";  
      int portNumber = 1433;  
      String databaseName = "AdventureWorks";   
      String user = "UserName";   
      String password = "*****";  
      String connectionUrl = prefix + serverName + ":" + portNumber  
         + ";databaseName=" + databaseName + ";user=" + user + ";password=" + password;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         Connection con = DriverManager.getConnection(connectionUrl);  
  
         // Create a test table.  
         Statement stmt = con.createStatement();  
         try {  
            stmt.executeUpdate("DROP TABLE XAMin");   
         }  
         catch (Exception e) {  
         }  
         stmt.executeUpdate("CREATE TABLE XAMin (f1 int, f2 varchar(max))");  
         stmt.close();  
         con.close();  
  
         // Create the XA data source and XA ready connection.  
         SQLServerXADataSource ds = new SQLServerXADataSource();  
         ds.setUser(user);  
         ds.setPassword(password);  
         ds.setServerName(serverName);  
         ds.setPortNumber(portNumber);  
         ds.setDatabaseName(databaseName);  
         XAConnection xaCon = ds.getXAConnection();  
         con = xaCon.getConnection();  
  
         // Get a unique Xid object for testing.  
         XAResource xaRes = null;  
         Xid xid = null;  
         xid = XidImpl.getUniqueXid(1);  
  
         // Get the XAResource object and set the timeout value.  
         xaRes = xaCon.getXAResource();  
         xaRes.setTransactionTimeout(0);  
  
         // Perform the XA transaction.  
         System.out.println("Write -> xid = " + xid.toString());  
         xaRes.start(xid,XAResource.TMNOFLAGS);  
         PreparedStatement pstmt =   
         con.prepareStatement("INSERT INTO XAMin (f1,f2) VALUES (?, ?)");  
         pstmt.setInt(1,1);  
         pstmt.setString(2,xid.toString());  
         pstmt.executeUpdate();  
  
         // Commit the transaction.  
         xaRes.end(xid,XAResource.TMSUCCESS);  
         xaRes.commit(xid,true);  
  
         // Cleanup.  
         con.close();  
         xaCon.close();  
  
         // Open a new connection and read back the record to verify that it worked.  
         con = DriverManager.getConnection(connectionUrl);  
         ResultSet rs = con.createStatement().executeQuery("SELECT * FROM XAMin");  
         rs.next();  
         System.out.println("Read -> xid = " + rs.getString(2));  
         rs.close();  
         con.close();  
      }   
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
  
class XidImpl implements Xid {  
  
   public int formatId;  
   public byte[] gtrid;  
   public byte[] bqual;  
   public byte[] getGlobalTransactionId() {return gtrid;}  
   public byte[] getBranchQualifier() {return bqual;}  
   public int getFormatId() {return formatId;}  
  
   XidImpl(int formatId, byte[] gtrid, byte[] bqual) {  
      this.formatId = formatId;  
      this.gtrid = gtrid;  
      this.bqual = bqual;  
   }  
  
   public String toString() {  
      int hexVal;  
      StringBuffer sb = new StringBuffer(512);  
      sb.append("formatId=" + formatId);  
      sb.append(" gtrid(" + gtrid.length + ")={0x");  
      for (int i=0; i<gtrid.length; i++) {  
         hexVal = gtrid[i]&0xFF;  
         if ( hexVal < 0x10 )  
            sb.append("0" + Integer.toHexString(gtrid[i]&0xFF));  
         else  
            sb.append(Integer.toHexString(gtrid[i]&0xFF));  
         }  
         sb.append("} bqual(" + bqual.length + ")={0x");  
         for (int i=0; i<bqual.length; i++) {  
            hexVal = bqual[i]&0xFF;  
            if ( hexVal < 0x10 )  
               sb.append("0" + Integer.toHexString(bqual[i]&0xFF));  
            else  
               sb.append(Integer.toHexString(bqual[i]&0xFF));  
         }  
         sb.append("}");  
         return sb.toString();  
      }  
  
      // Returns a globally unique transaction id.  
      static byte [] localIP = null;  
      static int txnUniqueID = 0;  
      static Xid getUniqueXid(int tid) {  
  
      Random rnd = new Random(System.currentTimeMillis());  
      txnUniqueID++;  
      int txnUID = txnUniqueID;  
      int tidID = tid;  
      int randID = rnd.nextInt();  
      byte[] gtrid = new byte[64];  
      byte[] bqual = new byte[64];  
      if ( null == localIP) {  
         try {  
            localIP = Inet4Address.getLocalHost().getAddress();  
         }  
         catch ( Exception ex ) {  
            localIP =  new byte[] { 0x01,0x02,0x03,0x04 };  
         }  
      }  
      System.arraycopy(localIP,0,gtrid,0,4);  
      System.arraycopy(localIP,0,bqual,0,4);  
  
      // Bytes 4 -> 7 - unique transaction id.  
      // Bytes 8 ->11 - thread id.  
      // Bytes 12->15 - random number generated by using seed from current time in milliseconds.  
      for (int i=0; i<=3; i++) {  
         gtrid[i+4] = (byte)(txnUID%0x100);  
         bqual[i+4] = (byte)(txnUID%0x100);  
         txnUID >>= 8;  
         gtrid[i+8] = (byte)(tidID%0x100);  
         bqual[i+8] = (byte)(tidID%0x100);  
         tidID >>= 8;  
         gtrid[i+12] = (byte)(randID%0x100);  
         bqual[i+12] = (byte)(randID%0x100);  
         randID >>= 8;  
      }  
      return new XidImpl(0x1234, gtrid, bqual);  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのトランザクションの実行](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  

