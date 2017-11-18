---
title: "Always Encrypted の JDBC ドライバー API リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/10/2016
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 008db0dabc1b0488daaef63945442b666ee02fa1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Always Encrypted の JDBC ドライバー API リファレンス
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Always Encrypted を使用すると、クライアントは SQL Server に暗号化キーを開示することなく、クライアント アプリケーション内の機密データを暗号化することができます。 クライアント コンピューターにインストールされている、Always Encrypted が有効のドライバーは、SQL Server クライアント アプリケーション内の機密データを自動的に暗号化および暗号化解除することで、この処理を実行します。 ドライバーは、SQL Server にデータを渡す前に機密性の高い列のデータを暗号化し、アプリケーションに対するセマンティクスが維持されるように自動的にクエリを書き換えます。 同様に、ドライバーはクエリ結果に含まれている暗号化されたデータベース列に格納されているデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  Always Encrypted は、SQL Server 2016 での SQL Server 用 Microsoft JDBC Driver 6.0 でのみサポートされている以上はします。  
  
 Always Encrypted を使用するクライアント アプリケーションで使用するために、JDBC ドライバー API に対していくつかの新たな追加と変更が施されています。  
  
 **SQLServerConnection クラス**  
  
|名前|説明|  
|----------|-----------------|  
|新しい接続文字列キーワード:<br /><br /> columnEncryptionSetting|columnEncryptionSetting = Enabled columnEncryptionSetting や接続に対して Always Encrypted 機能を有効に無効になっていますそれを無効にします。 指定できる値は、Enabled または Disabled です。 既定値は Disabled です。|  
|新しいメソッド:<br /><br /> public static void setColumnEncryptionTrustedMasterKeyPaths (マップ < 文字列, 一覧\<文字列 >> trustedKeyPaths)<br /><br /> public static void updateColumnEncryptionTrustedMasterKeyPaths (文字列のサーバー リスト\<文字列 > trustedKeyPaths)<br /><br /> public static void removeColumnEncryptionTrustedMasterKeyPaths (文字列 server)|で信頼されたキー パスの一覧の設定/更新/削除のデータベース サーバーのできます。 アプリケーション クエリの処理中に、一覧にないキー パスをドライバーが受け取った場合、クエリは失敗します。 このプロパティは、セキュリティが侵害され、偽のキー パスを提供し、キー ストアの資格情報漏洩につながるおそれがある SQL Server を含めたセキュリティ攻撃に対して、セキュリティ保護をさらに強化します。|  
|新しいメソッド:<br /><br /> パブリックの静的なマップ < 文字列, 一覧\<文字列 >> getColumnEncryptionTrustedMasterKeyPaths()|データベース サーバーの信頼されたキー パスの一覧を返します。|  
|新しいメソッド:<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (マップ\<文字列、SQLServerColumnEncryptionKeyStoreProvider > clientKeyStoreProviders)|カスタム キー ストア プロバイダーを登録できます。 これは、キー ストア プロバイダー名をキー ストア プロバイダー実装にマップするディクショナリです。<br /><br /> JVM キーストアを使用するには、JVM キーストアの資格情報を使用して SQLServerColumnEncryptionJVMKeyStoreProvider オブジェクトをインスタンス化し、ドライバーに登録する必要があります。 このプロバイダーの名前は 'MSSQL_JVM_KEYSTORE' である必要があります。<br /><br /> Azure Key Vault ストアを使用するには、SQLServerColumnEncryptionAzureKeyStoreProvider オブジェクトをインスタンス化し、ドライバーに登録する必要があります。 このプロバイダーの名前は、'AZURE_KEY_VAULT' である必要があります。|
|パブリックの最終的なブール getSendTimeAsDatetime()|SendTimeAsDatetime 接続プロパティの設定を返します。|
|public void setSendTimeAsDatetime (ブール sendTimeAsDateTimeValue)|SendTimeAsDatetime 接続プロパティの設定を変更します。|

 **SQLServerConnectionPoolProxy クラス**
|名前|Description|  
|----------|-----------------|  
|パブリックの最終的なブール getSendTimeAsDatetime()|SendTimeAsDatetime 接続プロパティの設定を返します。|
|public void setSendTimeAsDatetime (ブール sendTimeAsDateTimeValue)|SendTimeAsDatetime 接続プロパティの設定を変更します。|
     
  
 **SQLServerDataSource クラス**  
  
|名前|Description|  
|----------|-----------------|  
|public void setColumnEncryptionSetting (文字列 columnEncryptionSetting)|データ ソース オブジェクトに対して Always Encrypted 機能を有効または無効にします。<br /><br /> 既定値は Disabled です。|  
|パブリック文字列 getColumnEncryptionSetting()|データ ソース オブジェクトに対して Always Encrypted 機能を取得します。|
|public void setKeyStoreAuthentication (文字列 keyStoreAuthentication)|キー ストアを識別する名前を設定します。 サポートされる値のみが、特定 Java キー ストアの"JavaKeyStorePassword"です。<br/><br/>既定値は null です。|
|パブリック文字列 getKeyStoreAuthentication()|データ ソース オブジェクトに対して keyStoreAuthentication 設定の値を取得します。|
|public void setKeyStoreSecret (文字列 keyStoreSecret)|Java キーストアのパスワードを設定します。 、Java キー ストア プロバイダーを、キー ストアとキーのパスワードを必要があります、同じであることに注意してください。 なお、keyStoreAuthentication を"JavaKeyStorePassword"に設定する必要があります。|
|public void setKeyStoreLocation (文字列 keyStoreLocation)|Java キーストアのファイル名を含む場所を設定します。 なお、keyStoreAuthentication を"JavaKeyStorePassword"に設定する必要があります。|
|パブリック文字列 getKeyStoreLocation()|Java キー ストアの keyStoreLocation を取得します。|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider クラス**  
  
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
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider クラス**  
  
 Azure Key Vault のキー ストア プロバイダーの実装です。 このクラスは、列マスター_キーとして Azure Key Vault に格納されたキーを使用できるようにします。  
  
 コンス トラクター  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerColumnEncryptionAzureKeyVaultProvider (SQLServerKeyVaultAuthenticationCallback authenticationCallback、ExecutorService executorService)|Azure Key Vault のキー ストア プロバイダー。  Azure Key Vault にキーのアクセス トークンを取得する SQLServerKeyVaultAuthenticationCallback インターフェイスの実装を提供する必要があります。|  
  
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
|SQLServerColumnEncryptionKeyStoreProvider|すべてのキー ストア プロバイダーの基本クラス。 カスタム プロバイダー必要がありますこのクラスから派生し、そのメンバー関数をオーバーライドして登録して SQLServerConnection を使用します。 registerColumnEncryptionKeyStoreProviders() です。|  
  
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
|public void setBigDecimal (int parameterIndex、x、int 型の有効桁数、BigDecimal int 型の小数点以下桁数)<br /><br /> パブリックの void setObject (int parameterIndex、オブジェクトの x、int targetSqlType、整数の有効桁数、int 型の小数点以下桁数)<br /><br /> パブリックの void setObject (int parameterIndex、オブジェクトの x、SQLType targetSqlType、整数の有効桁数、整数の小数点以下桁数)<br /><br /> パブリックの void setTime (int parameterIndex, x, int スケール java.sql.Time)<br /><br /> パブリックの void setTimestamp (int parameterIndex, x, int スケール java.sql.Timestamp) <br />パブリックの void setDateTimeOffset (int parameterIndex, x, int スケール microsoft.sql.DateTimeOffset)|有効桁数または小数点以下桁数の引数またはその両方固有のデータ型有効桁数を必要とし、スケール情報の Always Encrypted をサポートするには、これらのメソッドがオーバー ロードします。|  
|public void setMoney (int parameterIndex、BigDecimal x)<br /><br /> public void setSmallMoney (int parameterIndex、BigDecimal x)<br /><br /> パブリックの void setUniqueIdentifier (int parameterIndex、文字列の guid)<br /><br /> public void について (int parameterIndex java.sql.Timestamp x)<br /><br /> public void setSmallDateTime (int parameterIndex java.sql.Timestamp x)|これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 列にパラメーター値を送信するため既存 setTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド setDateTime() と setSmallDateTime() をそれぞれ使用します。|  
|パブリックの最終的な void setBigDecimal (int parameterIndex、x、int 型の有効桁数 BigDecimal、int 小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setMoney (int parameterIndex、x、ブール forceEncrypt BigDecimal)<br /><br /> パブリックの最終的な void setSmallMoney (int parameterIndex、x、ブール forceEncrypt BigDecimal)<br /><br /> パブリックの最終的な void setBoolean (int parameterIndex、ブール型の x、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setByte (int parameterIndex, x, boolean forceEncrypt byte)<br /><br /> パブリックの最終的な void setBytes (int parameterIndex、バイト x[]、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setUniqueIdentifier (int parameterIndex、文字列の guid、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setDouble (int parameterIndex、倍精度浮動小数点 x、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setFloat (int parameterIndex、x を浮動小数点、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setInt (parameterIndex の int、int 型の値、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setLong (int parameterIndex、時間の長い x、ブール forceEncrypt)<br /><br /> パブリックの最終的な setObject (int parameterIndex、オブジェクトの x、int targetSqlType、整数の有効桁数、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setObject (int parameterIndex、オブジェクトの x、SQLType targetSqlType、整数の精度、スケールの整数、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setShort (int parameterIndex、短い x、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setString (int parameterIndex、文字列 str ブール forceEncrypt)<br /><br /> パブリックの最終的な void setNString (int parameterIndex、文字列値、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTime (int parameterIndex、x、int スケール java.sql.Time ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTimestamp (int parameterIndex、x、int スケール java.sql.Timestamp ブール forceEncrypt)<br /><br /> パブリックの最終的な void setDateTimeOffset (int parameterIndex、x、int 型の小数点以下桁数、microsoft.sql.DateTimeOffset ブール forceEncrypt)<br /><br /> パブリックの最終的な void について (int parameterIndex, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの最終的な void setSmallDateTime (int parameterIndex, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの最終的な void setDate (int parameterIndex、x, java.util.Calendar cal java.sql.Date ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTime (int parameterIndex、x, java.util.Calendar cal java.sql.Time ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTimestamp (int parameterIndex、x, java.util.Calendar cal java.sql.Timestamp ブール forceEncrypt)|指定されたパラメーターを指定された java 値に設定します。<br /><br /> ブール forceEncrypt が設定されている場合は true、クエリにパラメーターが場合にのみ設定の指定の列が暗号化され、またはステートメントで、接続で Always Encrypted が有効になっています。<br /><br /> ブール forceEncrypt が false に設定されている場合、ドライバーはパラメーターの暗号化を強制しません。|  
  
 新規またはオーバー ロードされたメソッド**SQLServerCallableStatement**クラス  
  
|名前|Description|  
|----------|-----------------|  
|パブリックの void registerOutParameter (int parameterIndex、int sqlType、int 型の有効桁数、int 型の小数点以下桁数)<br /><br /> パブリックの void registerOutParameter (int parameterIndex、SQLType sqlType、int 型の有効桁数、int 型の小数点以下桁数)<br /><br /> パブリックの void registerOutParameter (文字列 parameterName、int sqlType、int 型の有効桁数、int 型の小数点以下桁数)<br /><br /> パブリックの void registerOutParameter (文字列 parameterName、SQLType sqlType、int 型の有効桁数、int 型の小数点以下桁数)<br />パブリックの void setBigDecimal (文字列 parameterName、BigDecimal bd、int 型の有効桁数、int 型の小数点以下桁数)<br /><br /> パブリックの void setTime (文字列 parameterName、java.sql.Time t、int 型の小数点以下桁数)<br /><br /> パブリックの void setTimestamp (文字列 parameterName、java.sql.Timestamp t、int 型の小数点以下桁数)<br /><br /> パブリックの void setDateTimeOffset (文字列 parameterName、microsoft.sql.DateTimeOffset t、int 型の小数点以下桁数)<br/><br/>パブリックの最終的な void setObject (文字列 sCol、オブジェクトの x、int targetSqlType、整数の有効桁数、int 型の小数点以下桁数)|有効桁数または小数点以下桁数の引数またはその両方固有のデータ型有効桁数を必要とし、スケール情報の Always Encrypted をサポートするには、これらのメソッドがオーバー ロードします。|  
|public void について (文字列 parameterName, java.sql.Timestamp x)<br /><br /> public void setSmallDateTime (文字列 parameterName, java.sql.Timestamp x)<br /><br /> パブリックの void setUniqueIdentifier (文字列のパラメーター名、文字列の guid)<br /><br /> パブリックの void setMoney (文字列 parameterName、BigDecimal bd)<br /><br /> パブリックの void setSmallMoney (文字列 parameterName、BigDecimal bd)<br/><br/>パブリック タイムスタンプ getDateTime (int index)<br/><br/>パブリック タイムスタンプ getDateTime (文字列 sCol)<br/><br/>パブリックのタイムスタンプ getDateTime (int インデックス、カレンダー cal)<br/><br/>パブリック タイムスタンプ getSmallDateTime (int index)<br/><br/>パブリック タイムスタンプ getSmallDateTime (文字列 sCol)<br/><br/>パブリックのタイムスタンプ getSmallDateTime (int インデックス、カレンダー cal)<br/><br/>パブリックのタイムスタンプ getSmallDateTime (文字列名、カレンダー cal)<br/><br/>パブリック BigDecimal getMoney (int index)<br/><br/>パブリック BigDecimal getMoney (文字列 sCol)<br/><br/>パブリック BigDecimal getSmallMoney (int index)<br/><br/>パブリック BigDecimal getSmallMoney (文字列 sCol)|これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 列にパラメーター値を送信するため既存 setTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド setDateTime() と setSmallDateTime() をそれぞれ使用します。|  
|パブリックの void setObject (文字列 parameterName、o、int n、int m、ブール forceEncrypt)<br /><br /> パブリックの void setObject (文字列パラメーター名、オブジェクトの obj、SQLType jdbcType、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> public void setDate (文字列 parameterName、x、予定表 c java.sql.Date ブール forceEncrypt)<br /><br /> パブリックの void setTime (文字列 parameterName、java.sql.Time t、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> public void setTime (文字列 parameterName、x、予定表 c の場合、java.sql.Time ブール forceEncrypt)<br /><br /> パブリックの void について (文字列 parameterName, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの void setDateTimeOffset (文字列 parameterName、microsoft.sql.DateTimeOffset t、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの void setSmallDateTime (文字列 parameterName, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの void setTimestamp (文字列 parameterName、java.sql.Timestamp t、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの void setTimestamp (文字列 parameterName, x, boolean forceEncrypt java.sql.Timestamp)<br /><br /> パブリックの void setUniqueIdentifier (文字列のパラメーター名、文字列の guid、ブール forceEncrypt)<br /><br /> パブリックの void setBytes (文字列 parameterName、バイト:operator[] b、ブール forceEncrypt)<br /><br /> パブリックの void setByte (文字列 parameterName、バイト b、ブール forceEncrypt)<br /><br /> パブリックの void setString (文字列 parameterName、string、boolean forceEncrypt)<br /><br /> パブリックの最終的な void setNString (文字列のパラメーター名、文字列値、ブール forceEncrypt)<br /><br /> パブリックの void setMoney (文字列 parameterName、BigDecimal bd、ブール forceEncrypt)<br /><br /> パブリックの void setSmallMoney (文字列 parameterName、BigDecimal bd、ブール forceEncrypt)<br /><br /> パブリックの void setBigDecimal (文字列 parameterName、BigDecimal bd、int 型の有効桁数、int 型の小数点以下桁数、ブール forceEncrypt)<br /><br /> パブリックの void setDouble (文字列のパラメーター名、double d、ブール forceEncrypt)<br /><br /> パブリックの void setFloat (文字列 parameterName、float f、ブール forceEncrypt)<br /><br /> public void setInt (文字列 parameterName, int i, boolean forceEncrypt)<br /><br /> パブリックの void setLong (文字列 parameterName、時間の長い l、ブール forceEncrypt)<br /><br /> パブリックの void setShort (文字列のパラメーター名、短い s、ブール forceEncrypt)<br /><br /> パブリックの void setBoolean (文字列 parameterNames、b をブール値、ブール forceEncrypt)<br/><br/>public void setTimeStamp (文字列 sCol、x、予定表 c java.sql.Timestamp ブール forceEncrypt)|指定されたパラメーターを指定された java 値に設定します。<br /><br /> ブール forceEncrypt が設定されている場合は true、クエリにパラメーターが場合にのみ設定の指定の列が暗号化され、またはステートメントで、接続で Always Encrypted が有効になっています。<br /><br /> ブール forceEncrypt が false に設定されている場合、ドライバーはパラメーターの暗号化を強制しません。|
 

 新規またはオーバー ロードされたメソッド**SQLServerResultSet**クラス  
  
|名前|Description|  
|----------|-----------------|  
|パブリック文字列 getUniqueIdentifier (int columnIndex)<br/><br/>パブリック文字列 getUniqueIdentifier (文字列 columnLabel)<br/><br/>   パブリック java.sql.Timestamp getDateTime (int columnIndex) <br/><br/> パブリック java.sql.Timestamp getDateTime (文字列 columnName)   <br/><br/> パブリック java.sql.Timestamp getDateTime (int columnIndex、カレンダー cal)   <br/><br/>パブリック java.sql.Timestamp getDateTime (文字列 colName、カレンダー cal)    <br/><br/>パブリック java.sql.Timestamp getSmallDateTime (int columnIndex)    <br/><br/> パブリック java.sql.Timestamp getSmallDateTime (文字列 columnName)   <br/><br/> パブリック java.sql.Timestamp getSmallDateTime (int columnIndex、カレンダー cal)   <br/><br/> パブリック java.sql.Timestamp getSmallDateTime (文字列 colName、カレンダー cal)   <br/><br/>  パブリック BigDecimal getMoney (int columnIndex)  <br/><br/> パブリック BigDecimal getMoney (文字列 columnName)   <br/><br/> パブリック BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  パブリック BigDecimal getSmallMoney (文字列 columnName)  <br/><br/>public void updateMoney (文字列 columnName、BigDecimal x)    <br/><br/>  public void updateSmallMoney (文字列 columnName、BigDecimal x)  <br/><br/>     public void updateDateTime (int インデックス java.sql.Timestamp x) <br/><br/> public void updateSmallDateTime (int インデックス java.sql.Timestamp x) |これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 の列を更新するため既存 updateTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド updateDateTime() と updateSmallDateTime() をそれぞれ使用します。|
|パブリックの void updateBoolean (int インデックス、ブール型の x、ブール forceEncrypt)  <br/><br/>  パブリックの void updateByte (int インデックス, x, boolean forceEncrypt byte)  <br/><br/>  パブリックの void updateShort (int インデックス、短い x、ブール forceEncrypt)  <br/><br/> パブリックの void updateInt (int インデックス, x, boolean forceEncrypt int)   <br/><br/>  パブリックの void updateLong (int インデックス、時間の長い x、ブール forceEncrypt)  <br/><br/> パブリックの void updateFloat (int インデックス、x を浮動小数点、ブール forceEncrypt)   <br/><br/> パブリックの void updateDouble (int インデックス、倍精度浮動小数点 x、ブール forceEncrypt)   <br/><br/> public void updateMoney (int index, x, boolean forceEncrypt BigDecimal)   <br/><br/>  public void updateMoney (文字列 columnName、x、ブール forceEncrypt BigDecimal)  <br/><br/> public void updateSmallMoney (int index, x, boolean forceEncrypt BigDecimal)   <br/><br/>  public void updateSmallMoney (文字列 columnName、x、ブール forceEncrypt BigDecimal)  <br/><br/> パブリックの void updateBigDecimal (int インデックス、x、整数の有効桁数 BigDecimal、整数小数点以下桁数、ブール forceEncrypt)   <br/><br/>  パブリックの void updateString (int columnIndex、文字列の文字列値、ブール forceEncrypt)  <br/><br/>  パブリックの void updateNString (int columnIndex、文字列 nString、ブール forceEncrypt)  <br/><br/>  パブリックの void updateNString (文字列 columnLabel、文字列 nString、ブール forceEncrypt)  <br/><br/> パブリックの void updateBytes (int index, バイト x[], ブール forceEncrypt)   <br/><br/>  パブリックの void updateDate (int インデックス, x, boolean forceEncrypt java.sql.Date)  <br/><br/> public void updateTime (int インデックス、x、整数スケール java.sql.Time ブール forceEncrypt)   <br/><br/> public void updateTimestamp (int インデックス、x、int スケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/> public void updateDateTime (int インデックス、x、整数スケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/> public void updateSmallDateTime (int インデックス、x、整数スケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/>  public void updateDateTimeOffset (int インデックス、x、整数の小数点以下桁数、microsoft.sql.DateTimeOffset ブール forceEncrypt)  <br/><br/> public void updateUniqueIdentifier (int インデックス、文字列、ブール forceEncrypt x)    <br/><br/>  パブリックの void updateObject (int インデックス、オブジェクトの x、int 型の有効桁数、int 小数点以下桁数、ブール forceEncrypt)  <br/><br/>  パブリックの void updateObject (int インデックス、オブジェクトの obj、SQLType targetSqlType、int 型の小数点以下桁数、ブール forceEncrypt)  <br/><br/> パブリックの void updateBoolean (文字列 columnName、ブール型の x、ブール forceEncrypt)    <br/><br/>  パブリックの void updateByte (文字列 columnName, x, boolean forceEncrypt byte)  <br/><br/>  パブリックの void updateShort (文字列 columnName、短い x、ブール forceEncrypt)  <br/><br/> パブリックの void updateInt (文字列 columnName, x, boolean forceEncrypt int)   <br/><br/>   パブリックの void updateLong (文字列 columnName、時間の長い x、ブール forceEncrypt) <br/><br/>  パブリックの void updateFloat (文字列 columnName、x を浮動小数点、ブール forceEncrypt)  <br/><br/>  パブリックの void updateDouble (文字列 columnName、倍精度浮動小数点 x、ブール forceEncrypt)  <br/><br/> public void updateBigDecimal (文字列 columnName、x、ブール forceEncrypt BigDecimal)   <br/><br/>  パブリックの void updateBigDecimal (文字列 columnName、x、整数の有効桁数 BigDecimal、整数小数点以下桁数、ブール forceEncrypt)  <br/><br/> public void updateString (文字列 columnName、文字列、ブール forceEncrypt x)   <br/><br/>  パブリックの void updateBytes (文字列 columnName、バイト x[]、ブール forceEncrypt)  <br/><br/> パブリックの void updateDate (文字列 columnName, x, boolean forceEncrypt java.sql.Date)   <br/><br/>  public void updateTime (文字列 columnName, x, int スケール java.sql.Time ブール forceEncrypt)  <br/><br/>  public void updateTimestamp (文字列 columnName, x, int スケール java.sql.Timestamp ブール forceEncrypt)  <br/><br/> public void updateDateTime (文字列 columnName, x, int スケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/>  public void updateSmallDateTime (文字列 columnName, x, int スケール java.sql.Timestamp ブール forceEncrypt)  <br/><br/>  public void updateDateTimeOffset (文字列 columnName、x、int 型の小数点以下桁数、microsoft.sql.DateTimeOffset ブール forceEncrypt)  <br/><br/>  public void updateUniqueIdentifier (文字列 columnName、文字列、ブール forceEncrypt x)<br/><br/>パブリックの void updateObject (文字列 columnName、オブジェクトの x、int 型の有効桁数、int 型の小数点以下桁数、ブール forceEncrypt)<br/><br/>パブリックの void updateObject (文字列 columnName オブジェクト obj、SQLType targetSqlType、int スケール ブール forceEncrypt)|指定された java 値に指定された列を更新します。<br/><br/>ブール forceEncrypt に設定されている場合は true、列にのみ設定されますが暗号化されていて、接続またはステートメントでは、Always Encrypted が有効です。<br/><br/>ブール forceEncrypt が false に設定されている場合、ドライバーはパラメーターの暗号化を強制しません。|

  
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
  
  

