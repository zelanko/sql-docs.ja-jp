---
title: Always Encrypted の JDBC ドライバー API リファレンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 1/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d44903f7d57dd24f8cad3463a87a54e5ab5c290f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833207"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Always Encrypted の JDBC ドライバー API リファレンス
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Always Encrypted を使用すると、クライアントは SQL Server に暗号化キーを開示することなく、クライアント アプリケーション内の機密データを暗号化することができます。 クライアント コンピューターにインストールされている、Always Encrypted が有効のドライバーは、SQL Server クライアント アプリケーション内の機密データを自動的に暗号化および暗号化解除することで、この処理を実行します。 ドライバーは、SQL Server にデータを渡す前に機密性の高い列のデータを暗号化し、アプリケーションに対するセマンティクスが維持されるように自動的にクエリを書き換えます。 同様に、ドライバーはクエリ結果に含まれている暗号化されたデータベース列に格納されているデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  Always Encrypted は、SQL Server 2016 での SQL Server 用 Microsoft JDBC Driver 6.0 でのみサポートされている以上はします。  
  
 ## <a name="always-encrypted-api-references"></a>Always Encrypted API リファレンス
 
 Always Encrypted を使用するクライアント アプリケーションで使用するために、JDBC ドライバー API に対していくつかの新たな追加と変更が施されています。  
  
 **SQLServerConnection クラス**  
  
|名前|Description|  
|----------|-----------------|  
|新しい接続文字列キーワード:<br /><br /> columnEncryptionSetting|columnEncryptionSetting = Enabled columnEncryptionSetting や接続に対して Always Encrypted 機能を有効に無効になっていますそれを無効にします。 指定できる値は、Enabled または Disabled です。 既定値は Disabled です。|  
|新しいメソッド:<br /><br /> public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)<br /><br /> public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)<br /><br /> public static void removeColumnEncryptionTrustedMasterKeyPaths (文字列 server)|で信頼されたキー パスの一覧の設定/更新/削除のデータベース サーバーのできます。 アプリケーション クエリの処理中に、一覧にないキー パスをドライバーが受け取った場合、クエリは失敗します。 このプロパティは、セキュリティが侵害され、偽のキー パスを提供し、キー ストアの資格情報漏洩につながるおそれがある SQL Server を含めたセキュリティ攻撃に対して、セキュリティ保護をさらに強化します。|  
|新しいメソッド:<br /><br /> パブリックの静的なマップ < 文字列, 一覧\<文字列 >> getColumnEncryptionTrustedMasterKeyPaths()|データベース サーバーの信頼されたキー パスの一覧を返します。|  
|新しいメソッド:<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (マップ\<文字列、SQLServerColumnEncryptionKeyStoreProvider > clientKeyStoreProviders)|カスタム キー ストア プロバイダーを登録できます。 これは、キー ストア プロバイダー名をキー ストア プロバイダー実装にマップするディクショナリです。<br /><br /> JVM キーストアを使用するには、JVM キーストアの資格情報を使用して SQLServerColumnEncryptionJVMKeyStoreProvider オブジェクトをインスタンス化し、ドライバーに登録する必要があります。 このプロバイダーの名前は 'MSSQL_JVM_KEYSTORE' である必要があります。<br /><br /> Azure Key Vault ストアを使用するには、SQLServerColumnEncryptionAzureKeyStoreProvider オブジェクトをインスタンス化し、ドライバーに登録する必要があります。 このプロバイダーの名前は、'AZURE_KEY_VAULT' である必要があります。|
|public final boolean getSendTimeAsDatetime()|SendTimeAsDatetime 接続プロパティの設定を返します。|
|public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)|SendTimeAsDatetime 接続プロパティの設定を変更します。|

 **SQLServerConnectionPoolProxy クラス**
|名前|Description|  
|----------|-----------------|  
|public final boolean getSendTimeAsDatetime()|SendTimeAsDatetime 接続プロパティの設定を返します。|
|public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)|SendTimeAsDatetime 接続プロパティの設定を変更します。|
     
  
 **SQLServerDataSource クラス**  
  
|名前|Description|  
|----------|-----------------|  
|public void setColumnEncryptionSetting (文字列 columnEncryptionSetting)|データ ソース オブジェクトに対して Always Encrypted 機能を有効または無効にします。<br /><br /> 既定値は Disabled です。|  
|パブリック文字列 getColumnEncryptionSetting()|データ ソース オブジェクトに対して Always Encrypted 機能を取得します。|
|public void setKeyStoreAuthentication(String keyStoreAuthentication)|キー ストアを識別する名前を設定します。 サポートされる値のみが、特定 Java キー ストアの"JavaKeyStorePassword"です。<br/><br/>既定値は null です。|
|public String getKeyStoreAuthentication()|データ ソース オブジェクトに対して keyStoreAuthentication 設定の値を取得します。|
|public void setKeyStoreSecret(String keyStoreSecret)|Java キーストアのパスワードを設定します。 、Java キー ストア プロバイダーを、キー ストアとキーのパスワードを必要があります、同じであることに注意してください。 なお、keyStoreAuthentication を"JavaKeyStorePassword"に設定する必要があります。|
|public void setKeyStoreLocation(String keyStoreLocation)|Java キーストアのファイル名を含む場所を設定します。 なお、keyStoreAuthentication を"JavaKeyStorePassword"に設定する必要があります。|
|public String getKeyStoreLocation()|Java キー ストアの keyStoreLocation を取得します。|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider Class**  
  
 Java キー ストアのキー ストア プロバイダーの実装です。 このクラスは、列マスター_キーとして Java キーストアに格納されている証明書を使用できるようにします。  
  
 コンス トラクター  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerColumnEncryptionJavaKeyStoreProvider (文字列 keyStoreLocation、char keyStoreSecret)|Java キー ストアのキー ストア プロバイダー。|  
  
 メソッド  
  
|名前|Description|  
|----------|-----------------|  
|パブリック バイト:operator[] decryptColumnEncryptionKey (文字列 masterKeyPath、文字列の encryptionAlgorithm、バイト:operator[] encryptedColumnEncryptionKey)|列暗号化キーの暗号化された指定値を暗号化解除します。 暗号化された値は、指定したキー パスと共に証明書を使用し、指定したアルゴリズムを使用して、暗号化されることが想定されています。<br /><br /> **キーのパスの形式は、次のいずれかにする必要があります。**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (SQLServerColumnEncryptionKeyStoreProvider をオーバーライドします。 decryptColumnEncryptionKey (, String, Byte[]).)|  
|パブリック バイト:operator[] encryptColumnEncryptionKey (文字列 masterKeyPath、文字列の encryptionAlgorithm、バイト:operator[] plainTextColumnEncryptionKey)|指定したキー パスと共に証明書を使用し、指定したアルゴリズムを使用して、列暗号化キーを暗号化します。<br /><br /> **キーのパスの形式は、次のいずれかにする必要があります。**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (SQLServerColumnEncryptionKeyStoreProvider をオーバーライドします。 (, String, Byte[]).) encryptColumnEncryptionKey|  
|public void setName (文字列名)|このキー ストア プロバイダーの名前を設定します。|
|パブリック String getName)|このキー ストア プロバイダーの名前を取得します。|
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider Class**  
  
 Azure Key Vault のキー ストア プロバイダーの実装です。 このクラスは、列マスター_キーとして Azure Key Vault に格納されたキーを使用できるようにします。  
  
 コンス トラクター  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerColumnEncryptionAzureKeyVaultProvider (文字列 clientId, 文字列 clientKey)|Azure Key Vault のキー ストア プロバイダー。  識別子と Azure Key Vault への認証トークンを要求して、クライアントのキーを指定する必要があります。|  
  
 メソッド  
  
|名前|Description|  
|----------|-----------------|  
|パブリック バイト:operator[] decryptColumnEncryptionKey (文字列 masterKeyPath、文字列の encryptionAlgorithm、バイト:operator[] encryptedColumnEncryptionKey)|列暗号化キーの暗号化された指定値を暗号化解除します。 暗号化された値は、暗号化された指定した列のキーを IDmaster アルゴリズムを使用して、指定されたをすると想定されます。 <br />(SQLServerColumnEncryptionKeyStoreProvider をオーバーライドします。 decryptColumnEncryptionKey (, String, Byte[]).)|  
|パブリック バイト:operator[] encryptColumnEncryptionKey (文字列 masterKeyPath、文字列の encryptionAlgorithm、バイト:operator[] columnEncryptionKey)|指定したアルゴリズムを使用して、指定された列のマスター _ キー列の暗号化キーを暗号化します。 <br />(SQLServerColumnEncryptionKeyStoreProvider をオーバーライドします。 (, String, Byte[]).) encryptColumnEncryptionKey|  
|public void setName (文字列名)|このキー ストア プロバイダーの名前を設定します。|
|パブリック String getName)|このキー ストア プロバイダーの名前を取得します。|  
  
  
 **SQLServerKeyVaultAuthenticationCallback インターフェイス**  
  
 このインターフェイスには、ユーザーによって実装されるは、Azure Key Vault 認証用の 1 つのメソッドが含まれています。  
  
 メソッド  
  
|名前|Description|  
|----------|-----------------|  
|パブリックの文字列 getAccessToken (文字列機関、文字列リソース、文字列のスコープ) です。|メソッドをオーバーライドする必要があります。 メソッドは、トークンを Azure Key Vault にアクセスするために使用されます。|  
  
 **SQLServerColumnEncryptionKeyStoreProvider クラス**  
  
 カスタム キー ストア プロバイダーを実装するには、このクラスを拡張します。  
  
|名前|Description|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|すべてのキー ストア プロバイダーの基本クラス。 カスタム プロバイダー必要がありますこのクラスから派生し、そのメンバー関数をオーバーライドして登録して SQLServerConnection を使用します。 registerColumnEncryptionKeyStoreProviders().|  
  
 メソッド  
  
|名前|Description|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|列暗号化キーの暗号化された指定値を暗号化解除するための基本クラス メソッド。 暗号化された値は、指定したキー パスと共に列マスター キーを使用し、指定したアルゴリズムを使用して、暗号化されることが想定されています。|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|指定したキー パスと共に列マスター キーを使用し、指定したアルゴリズムを使用して、列暗号化キーを暗号化するための基本クラス メソッド。|
|パブリックの抽象 void setName (文字列名)|このキー ストア プロバイダーの名前を設定します。|
|パブリックの抽象文字列 getName()|このキー ストア プロバイダーの名前を取得します。|  
  
 新規またはオーバー ロードされたメソッド**SQLServerPreparedStatement**クラス  
  
|名前|Description|  
|----------|-----------------|  
|public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)<br /><br /> public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)<br /><br /> public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)<br /><br /> public void setTime(int parameterIndex, java.sql.Time x, int scale)<br /><br /> public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale) <br />パブリックの void setDateTimeOffset (int parameterIndex, x, int スケール microsoft.sql.DateTimeOffset)|有効桁数または小数点以下桁数の引数またはその両方固有のデータ型有効桁数を必要とし、スケール情報の Always Encrypted をサポートするには、これらのメソッドがオーバー ロードします。|  
|public void setMoney(int parameterIndex, BigDecimal x)<br /><br /> public void setSmallMoney(int parameterIndex, BigDecimal x)<br /><br /> public void setUniqueIdentifier(int parameterIndex, String guid)<br /><br /> public void setDateTime(int parameterIndex, java.sql.Timestamp x)<br /><br /> public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)|これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 列にパラメーター値を送信するため既存 setTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド setDateTime() と setSmallDateTime() をそれぞれ使用します。|  
|public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)<br /><br /> public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)<br /><br /> パブリックの最終的な void setSmallMoney (int parameterIndex、x、ブール forceEncrypt BigDecimal)<br /><br /> public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)<br /><br /> public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)<br /><br /> public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)<br /><br /> public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)<br /><br /> public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)<br /><br /> public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)<br /><br /> public final void setInt(int parameterIndex, int value, boolean forceEncrypt)<br /><br /> public final void setLong(int parameterIndex, long x, boolean forceEncrypt)<br /><br /> パブリックの最終的な setObject (int parameterIndex、オブジェクトの x、int targetSqlType、整数の有効桁数、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)<br /><br /> public final void setShort(int parameterIndex, short x, boolean forceEncrypt)<br /><br /> public final void setString(int parameterIndex, String str, boolean forceEncrypt)<br /><br /> public final void setNString(int parameterIndex, String value, boolean forceEncrypt)<br /><br /> public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)<br /><br /> パブリックの最終的な void setTimestamp (int parameterIndex、x、int スケール java.sql.Timestamp ブール forceEncrypt)<br /><br /> パブリックの最終的な void setDateTimeOffset (int parameterIndex、x、int 型の小数点以下桁数、microsoft.sql.DateTimeOffset ブール forceEncrypt)<br /><br /> public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)<br /><br /> public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)<br /><br /> public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)<br /><br /> public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)<br /><br /> パブリックの最終的な void setTimestamp (int parameterIndex、x, java.util.Calendar cal java.sql.Timestamp ブール forceEncrypt)|指定されたパラメーターを指定された java 値に設定します。<br /><br /> ブール forceEncrypt が設定されている場合は true、クエリにパラメーターが場合にのみ設定の指定の列が暗号化され、またはステートメントで、接続で Always Encrypted が有効になっています。<br /><br /> ブール forceEncrypt が false に設定されている場合、ドライバーはパラメーターの暗号化を強制しません。|  
  
 新規またはオーバー ロードされたメソッド**SQLServerCallableStatement**クラス  
  
|名前|Description|  
|----------|-----------------|  
|public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)<br />パブリックの void setBigDecimal (文字列 parameterName、BigDecimal bd、int 型の有効桁数、int 型の小数点以下桁数)<br /><br /> public void setTime(String parameterName, java.sql.Time t, int scale)<br /><br /> パブリックの void setTimestamp (文字列 parameterName、java.sql.Timestamp t、int 型の小数点以下桁数)<br /><br /> パブリックの void setDateTimeOffset (文字列 parameterName、microsoft.sql.DateTimeOffset t、int 型の小数点以下桁数)<br/><br/>パブリックの最終的な void setObject (文字列 sCol、オブジェクトの x、int targetSqlType、整数の有効桁数、int 型の小数点以下桁数)|有効桁数または小数点以下桁数の引数またはその両方固有のデータ型有効桁数を必要とし、スケール情報の Always Encrypted をサポートするには、これらのメソッドがオーバー ロードします。|  
|public void について (文字列 parameterName, java.sql.Timestamp x)<br /><br /> public void setSmallDateTime (文字列 parameterName, java.sql.Timestamp x)<br /><br /> public void setUniqueIdentifier(String parameterName, String guid)<br /><br /> パブリックの void setMoney (文字列 parameterName、BigDecimal bd)<br /><br /> パブリックの void setSmallMoney (文字列 parameterName、BigDecimal bd)<br/><br/>パブリック タイムスタンプ getDateTime (int index)<br/><br/>パブリック タイムスタンプ getDateTime (文字列 sCol)<br/><br/>パブリックのタイムスタンプ getDateTime (int インデックス、カレンダー cal)<br/><br/>public Timestamp getSmallDateTime(int index)<br/><br/>パブリック タイムスタンプ getSmallDateTime (文字列 sCol)<br/><br/>パブリックのタイムスタンプ getSmallDateTime (int インデックス、カレンダー cal)<br/><br/>パブリックのタイムスタンプ getSmallDateTime (文字列名、カレンダー cal)<br/><br/>パブリック BigDecimal getMoney (int index)<br/><br/>パブリック BigDecimal getMoney (文字列 sCol)<br/><br/>パブリック BigDecimal getSmallMoney (int index)<br/><br/>パブリック BigDecimal getSmallMoney (文字列 sCol)|これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 列にパラメーター値を送信するため既存 setTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド setDateTime() と setSmallDateTime() をそれぞれ使用します。|  
|パブリックの void setObject (文字列 parameterName、o、int n、int m、ブール forceEncrypt)<br /><br /> パブリックの void setObject (文字列パラメーター名、オブジェクトの obj、SQLType jdbcType、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> public void setDate (文字列 parameterName、x、予定表 c java.sql.Date ブール forceEncrypt)<br /><br /> public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)<br /><br /> public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)<br /><br /> パブリックの void について (文字列 parameterName, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの void setDateTimeOffset (文字列 parameterName、microsoft.sql.DateTimeOffset t、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの void setSmallDateTime (文字列 parameterName, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの void setTimestamp (文字列 parameterName、java.sql.Timestamp t、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの void setTimestamp (文字列 parameterName, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)<br /><br /> パブリックの void setBytes (文字列 parameterName、バイト:operator[] b、ブール forceEncrypt)<br /><br /> パブリックの void setByte (文字列 parameterName、バイト b、ブール forceEncrypt)<br /><br /> パブリックの void setString (文字列 parameterName、string、boolean forceEncrypt)<br /><br /> パブリックの最終的な void setNString (文字列のパラメーター名、文字列値、ブール forceEncrypt)<br /><br /> パブリックの void setMoney (文字列 parameterName、BigDecimal bd、ブール forceEncrypt)<br /><br /> パブリックの void setSmallMoney (文字列 parameterName、BigDecimal bd、ブール forceEncrypt)<br /><br /> パブリックの void setBigDecimal (文字列 parameterName、BigDecimal bd、int 型の有効桁数、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの void setDouble (文字列のパラメーター名、double d、ブール forceEncrypt)<br /><br /> パブリックの void setFloat (文字列 parameterName、float f、ブール forceEncrypt)<br /><br /> public void setInt (文字列 parameterName, int i, boolean forceEncrypt)<br /><br /> パブリックの void setLong (文字列 parameterName、時間の長い l、ブール forceEncrypt)<br /><br /> パブリックの void setShort (文字列のパラメーター名、短い s、ブール forceEncrypt)<br /><br /> パブリックの void setBoolean (文字列 parameterNames、b をブール値、ブール forceEncrypt)<br/><br/>public void setTimeStamp (文字列 sCol、x、予定表 c java.sql.Timestamp ブール forceEncrypt)|指定されたパラメーターを指定された java 値に設定します。<br /><br /> ブール forceEncrypt が設定されている場合は true、クエリにパラメーターが場合にのみ設定の指定の列が暗号化され、またはステートメントで、接続で Always Encrypted が有効になっています。<br /><br /> ブール forceEncrypt が false に設定されている場合、ドライバーはパラメーターの暗号化を強制しません。|
 

 新規またはオーバー ロードされたメソッド**SQLServerResultSet**クラス  
  
|名前|Description|  
|----------|-----------------|  
|public String getUniqueIdentifier(int columnIndex)<br/><br/>パブリック文字列 getUniqueIdentifier (文字列 columnLabel)<br/><br/>   public java.sql.Timestamp getDateTime(int columnIndex) <br/><br/> public java.sql.Timestamp getDateTime(String columnName)   <br/><br/> public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)   <br/><br/>public java.sql.Timestamp getDateTime(String colName, Calendar cal)    <br/><br/>public java.sql.Timestamp getSmallDateTime(int columnIndex)    <br/><br/> public java.sql.Timestamp getSmallDateTime(String columnName)   <br/><br/> public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)   <br/><br/> public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)   <br/><br/>  パブリック BigDecimal getMoney (int columnIndex)  <br/><br/> パブリック BigDecimal getMoney (文字列 columnName)   <br/><br/> パブリック BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  パブリック BigDecimal getSmallMoney (文字列 columnName)  <br/><br/>public void updateMoney(String columnName, BigDecimal x)    <br/><br/>  public void updateSmallMoney(String columnName, BigDecimal x)  <br/><br/>     public void updateDateTime(int index, java.sql.Timestamp x) <br/><br/> public void updateSmallDateTime(int index, java.sql.Timestamp x) |これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 の列を更新するため既存 updateTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド updateDateTime() と updateSmallDateTime() をそれぞれ使用します。|
|public void updateBoolean(int index, boolean x, boolean forceEncrypt)  <br/><br/>  public void updateByte(int index, byte x, boolean forceEncrypt)  <br/><br/>  public void updateShort(int index, short x, boolean forceEncrypt)  <br/><br/> public void updateInt(int index, int x, boolean forceEncrypt)   <br/><br/>  public void updateLong(int index, long x, boolean forceEncrypt)  <br/><br/> public void updateFloat(int index, float x, boolean forceEncrypt)   <br/><br/> public void updateDouble(int index, double x, boolean forceEncrypt)   <br/><br/> public void updateMoney (int index, x, boolean forceEncrypt BigDecimal)   <br/><br/>  public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)  <br/><br/> public void updateSmallMoney (int index, x, boolean forceEncrypt BigDecimal)   <br/><br/>  public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)   <br/><br/>  public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)  <br/><br/>  public void updateNString(int columnIndex, String nString, boolean forceEncrypt)  <br/><br/>  パブリックの void updateNString (文字列 columnLabel、文字列 nString、ブール forceEncrypt)  <br/><br/> public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)  <br/><br/> public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)   <br/><br/> public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)   <br/><br/> public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)   <br/><br/> public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)   <br/><br/>  public void updateDateTimeOffset (int インデックス、x、整数の小数点以下桁数、microsoft.sql.DateTimeOffset ブール forceEncrypt)  <br/><br/> public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)    <br/><br/>  public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)  <br/><br/>  public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)  <br/><br/> パブリックの void updateBoolean (文字列 columnName、ブール型の x、ブール forceEncrypt)    <br/><br/>  パブリックの void updateByte (文字列 columnName, x, boolean forceEncrypt byte)  <br/><br/>  public void updateShort(String columnName, short x, boolean forceEncrypt)  <br/><br/> public void updateInt(String columnName, int x, boolean forceEncrypt)   <br/><br/>   public void updateLong(String columnName, long x, boolean forceEncrypt) <br/><br/>  パブリックの void updateFloat (文字列 columnName、x を浮動小数点、ブール forceEncrypt)  <br/><br/>  public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal (文字列 columnName、x、ブール forceEncrypt BigDecimal)   <br/><br/>  パブリックの void updateBigDecimal (文字列 columnName、x、整数の有効桁数 BigDecimal、整数小数点以下桁数、ブール forceEncrypt)  <br/><br/> public void updateString(String columnName, String x, boolean forceEncrypt)   <br/><br/>  パブリックの void updateBytes (文字列 columnName、バイト x[]、ブール forceEncrypt)  <br/><br/> public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)   <br/><br/>  public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)  <br/><br/>  public void updateTimestamp (文字列 columnName, x, int スケール java.sql.Timestamp ブール forceEncrypt)  <br/><br/> public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)   <br/><br/>  public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)  <br/><br/>  public void updateDateTimeOffset (文字列 columnName、x、int 型の小数点以下桁数、microsoft.sql.DateTimeOffset ブール forceEncrypt)  <br/><br/>  public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)<br/><br/>public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)<br/><br/>public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)|指定された java 値に指定された列を更新します。<br/><br/>ブール forceEncrypt に設定されている場合は true、列にのみ設定されますが暗号化されていて、接続またはステートメントでは、Always Encrypted が有効です。<br/><br/>ブール forceEncrypt が false に設定されている場合、ドライバーはパラメーターの暗号化を強制しません。|

  
新しい型**microsoft.sql.Types**クラス
|名前|Description|  
|----------|-----------------|  
|DATETIME、SMALLDATETIME、MONEY、SMALLMONEY、GUID|対象の SQL 型としてこれらの型を使用するパラメーターの値を送信するときに**暗号化**datetime、smalldatetime、money、smallmoney、setObject()/updateObject() API メソッドを使用して uniqueidentifier 列です。|  
  
  
 **SQLServerStatementColumnEncryptionSetting 列挙型**  
  
 データの送信し、受信した暗号化された列を読み書きするときに指定します。 によっては、特定のクエリには、Always Encrypted のドライバーの暗号化されていない列を使用するときの処理をバイパスするによりパフォーマンスに与える影響を小さく可能性があります。 暗号化をバイパスし、プレーン テキスト データにアクセスできるようにこれらの設定を使用できないことに注意してください。  
  
 **構文**  
  
```  
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **メンバー**  
  
|名前|Description|  
|----------|-----------------|  
|UseConnectionSetting|コマンドが既定として設定する接続文字列内の Always Encrypted 設定を指定します。|  
|有効|クエリの Always Encrypted を有効にします。|  
|ResultSetOnly|コマンドの結果のみが、ドライバーで Always Encrypted ルーチンによって処理されることを指定します。 この値は、コマンドに暗号化を必要とするパラメーターがあるないときに使用します。|  
|Disabled|クエリの Always Encrypted を無効にします。|  
  
 AE をステートメント レベルの設定は、SQLServerConnection クラスして SQLServerConnectionPoolProxy クラスに追加されます。 新しい設定では、これらのクラスに次のメソッドがオーバー ロードします。  
  
|名前|Description|  
|----------|-----------------|  
|パブリックのステートメント createStatement (int タイプ int nConcur、int statementHoldability SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|特定の種類、同時実行、保持機能および列の暗号化設定で結果セット オブジェクトを生成するステートメント オブジェクトを作成します。|  
|パブリックの CallableStatement prepareCall (文字列 sql int タイプ、int nConcur、int statementHoldability SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|特定の種類、同時実行および保持機能を持つ結果セット オブジェクトを生成する、指定された列暗号化設定では、CallableStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (文字列 sql、int autogeneratedKeys、SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|自動生成キーを取得する機能を持つ、指定された列暗号化設定では、PreparedStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (文字列 sql、文字列 columnNames、SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|指定された列名を持つ結果セット オブジェクトを生成する、指定された列暗号化設定では、PreparedStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (文字列 sql int:operator[] columnIndexes、SQLServerStatementColumnEncryptionSetting stmtColEncSetting|指定した列のインデックスを持つ結果セット オブジェクトを生成する、指定された列暗号化設定では、PreparedStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (文字列 sql int タイプ、int nConcur、int nHold SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|特定の種類、同時実行および保持機能を持つ結果セット オブジェクトを生成する、指定された列暗号化設定では、PreparedStatement オブジェクトを作成します。|  
  
> [!NOTE]  
>  クエリの Always Encrypted が無効になっているし、クエリがパラメーターである暗号化された (暗号化された列に対応する) 必要があるパラメーター、クエリは失敗します。  
>   
>  クエリの Always Encrypted が無効になっている、クエリは、暗号化された列から結果を返す場合は、クエリは暗号化された値を返します。 暗号化された値は、varbinary データ型があります。  
  
 ## <a name="see-also"></a>参照  
 [JDBC ドライバーで Always Encrypted を使用する](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

