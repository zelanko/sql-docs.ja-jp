---
title: JDBC ドライバーの Always Encrypted API のリファレンス | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
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
ms.openlocfilehash: f1b720a607b702e93643d70b40a5e6ab036f2f56
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279253"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>JDBC ドライバーの Always Encrypted API のリファレンス
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Always Encrypted を使用すると、クライアントは SQL Server に暗号化キーを開示することなく、クライアント アプリケーション内の機密データを暗号化することができます。 クライアント コンピューターにインストールされている、Always Encrypted が有効のドライバーは、SQL Server クライアント アプリケーション内の機密データを自動的に暗号化および暗号化解除することで、この機能を実行します。 ドライバーは、SQL Server にデータを渡す前に機密性の高い列のデータを暗号化し、アプリケーションに対するセマンティクスが維持されるように自動的にクエリを書き換えます。 同様に、ドライバーはクエリ結果内の暗号化されたデータベース列に格納されているデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)します。  
  
> [!NOTE]  
>  Always Encrypted は、SQL Server 2016 で使用される Microsoft JDBC Driver 6.0 for SQL Server 以降でのみサポートされています。  
  
 ## <a name="always-encrypted-api-references"></a>Always Encrypted API リファレンス
 
 Always Encrypted を使用するクライアント アプリケーションで使用するために、JDBC ドライバー API に対していくつかの新たな追加と変更が施されています。  
  
 **SQLServerConnection クラス**  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|新しい接続文字列キーワード:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled は接続で Always Encrypted 機能を有効にし、columnEncryptionSetting=Disabled はこの機能を無効にします。 指定できる値は、Enabled または Disabled です。 既定値は Disabled です。|  
|新しいメソッド:<br /><br /> パブリックの静的 void setColumnEncryptionTrustedMasterKeyPaths (マップ < 文字列, 一覧\<文字列 >> trustedKeyPaths)<br /><br /> パブリックの静的 void updateColumnEncryptionTrustedMasterKeyPaths (文字列のサーバー、リスト\<文字列 > trustedKeyPaths)<br /><br /> パブリック静的 void removeColumnEncryptionTrustedMasterKeyPaths (文字列のサーバー)|データベース サーバーの信頼されたキー パスの一覧を設定、更新、削除できます。 アプリケーション クエリの処理中に、一覧にないキー パスをドライバーが受け取った場合、クエリは失敗します。 このプロパティは、セキュリティが侵害され、偽のキー パスを送信し、キー ストアの資格情報漏洩につながるおそれがある SQL Server を含めたセキュリティ攻撃に対して、セキュリティ保護をさらに強化します。|  
|新しいメソッド:<br /><br /> public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()|データベース サーバーの信頼されたキー パスの一覧を返します。|  
|新しいメソッド:<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)|カスタム キー ストア プロバイダーを登録できます。 これは、キー ストア プロバイダー名をキー ストア プロバイダー実装にマップするディクショナリです。<br /><br /> JVM キーストアを使用するには、JVM キーストアの資格情報を使用して SQLServerColumnEncryptionJVMKeyStoreProvider オブジェクトをインスタンス化し、ドライバーに登録する必要があります。 このプロバイダーの名前は ‘MSSQL_JVM_KEYSTORE’ である必要があります。<br /><br /> Azure Key Vault ストアを使用するには、SQLServerColumnEncryptionAzureKeyStoreProvider オブジェクトをインスタンス化し、ドライバーに登録する必要があります。 このプロバイダーの名前は、'AZURE_KEY_VAULT' である必要があります。|
|public final boolean getSendTimeAsDatetime()|SendTimeAsDatetime 接続プロパティの設定を返します。|
|public void setSendTimeAsDatetime (ブール sendTimeAsDateTimeValue)|SendTimeAsDatetime 接続プロパティの設定を変更します。|

 **SQLServerConnectionPoolProxy クラス**
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|public final boolean getSendTimeAsDatetime()|SendTimeAsDatetime 接続プロパティの設定を返します。|
|public void setSendTimeAsDatetime (ブール sendTimeAsDateTimeValue)|SendTimeAsDatetime 接続プロパティの設定を変更します。|
     
  
 **SQLServerDataSource クラス**  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|public void setColumnEncryptionSetting(String columnEncryptionSetting)|データ ソース オブジェクトに対して Always Encrypted 機能を有効または無効にします。<br /><br /> 既定値は Disabled です。|  
|パブリック文字列 getColumnEncryptionSetting()|データ ソース オブジェクトに対して Always Encrypted 機能を取得します。|
|public void setKeyStoreAuthentication (文字列 keyStoreAuthentication)|キー ストアを識別する名前を設定します。 サポートされる値のみが、 **JavaKeyStorePassword** Java キー ストアを識別するためです。<br/><br/>既定値は null です。|
|パブリック文字列 getKeyStoreAuthentication()|データ ソース オブジェクトの keyStoreAuthentication 設定の値を取得します。|
|public void setKeyStoreSecret (文字列 keyStoreSecret)|Java キーストアのパスワードを設定します。 キーストアとキーのパスワードは同じである必要があります。 その keyStoreAuthentication を設定する必要がありますに注意してください。 **JavaKeyStorePassword**します。|
|public void setKeyStoreLocation (文字列 keyStoreLocation)|Java キーストアのファイル名を含む場所を設定します。 その keyStoreAuthentication を設定する必要がありますに注意してください。 **JavaKeyStorePassword**します。|
|パブリック文字列 getKeyStoreLocation()|Java キー ストアの keyStoreLocation を取得します。|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider クラス**  
  
 Java キー ストアにキー ストア プロバイダーを実装します。 このクラスは、Java キー ストアに格納されている証明書を列マスター キーとして使用できるようにします。  
  
 コンストラクター  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|パブリック SQLServerColumnEncryptionJavaKeyStoreProvider (文字列 keyStoreLocation、char keyStoreSecret)|Java キー ストアのキー ストア プロバイダー。|  
  
 メソッド  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|列暗号化キーの暗号化された指定値を暗号化解除します。 暗号化された値は、指定したキー パスと共に証明書を使用し、指定したアルゴリズムを使用して、暗号化されることが想定されています。<br /><br /> **キー パスの書式は次のいずれかになります。**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (SQLServerColumnEncryptionKeyStoreProvider.decryptColumnEncryptionKey(String, String, Byte[]) をオーバーライドします) decryptColumnEncryptionKey (, String, byte[]|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)|指定したキー パスと共に証明書を使用し、指定したアルゴリズムを使用して、列暗号化キーを暗号化します。<br /><br /> **キー パスの書式は次のいずれかになります。**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (SQLServerColumnEncryptionKeyStoreProvider.encryptColumnEncryptionKey(String, String, Byte[]) をオーバーライドします) (, String, byte[] encryptColumnEncryptionKey|  
|public void setName (文字列名)|このキー ストア プロバイダーの名前を設定します。|
|public String getName ()|このキー ストア プロバイダーの名前を取得します。|
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider クラス**  
  
 Azure Key Vault のキー ストア プロバイダーを実装します。 このクラスでは、列マスター_キーとして Azure Key Vault に格納されたキーを使用できるようにします。  
  
 コンストラクター  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|パブリック SQLServerColumnEncryptionAzureKeyVaultProvider (文字列 clientId, 文字列 clientkey では)|Azure Key Vault のキー ストア プロバイダー。  識別子と Azure Key Vault への認証トークンを要求して、クライアントのキーを指定する必要があります。|  
  
 メソッド  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|列暗号化キーの暗号化された指定値を暗号化解除します。 暗号化された値は、指定した列キー IDmaster キーと指定したアルゴリズムを使用して、暗号化されることが想定されています。 <br />(SQLServerColumnEncryptionKeyStoreProvider.decryptColumnEncryptionKey(String, String, Byte[]) をオーバーライドします) decryptColumnEncryptionKey (, String, byte[]|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)|指定した列マスター キーと指定したアルゴリズムを使用して列暗号化キーを暗号化します。 <br />(SQLServerColumnEncryptionKeyStoreProvider.encryptColumnEncryptionKey(String, String, Byte[]) をオーバーライドします) (, String, byte[] encryptColumnEncryptionKey|  
|public void setName (文字列名)|このキー ストア プロバイダーの名前を設定します。|
|public String getName ()|このキー ストア プロバイダーの名前を取得します。|  
  
  
 **SQLServerKeyVaultAuthenticationCallback インターフェイス**  
  
 このインターフェイスには、Azure Key Vault の認証は、ユーザーによって実装されるは 1 つのメソッドが含まれています。  
  
 メソッド  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|パブリック文字列 getAccessToken (文字列機関、文字列リソース、文字列の範囲)|メソッドをオーバーライドする必要があります。 メソッドは、トークンを Azure Key Vault にアクセスするために使用されます。|  
  
 **SQLServerColumnEncryptionKeyStoreProvider クラス**  
  
 カスタム キー ストア プロバイダーを実装するには、このクラスを拡張します。  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|すべてのキー ストア プロバイダーの基本クラス。 カスタム プロバイダーはこのクラスから派生し、そのメンバー関数をオーバーライドしてから、SQLServerConnection.registerColumnEncryptionKeyStoreProviders() を使用して登録する必要があります。 registerColumnEncryptionKeyStoreProviders() します。|  
  
 メソッド  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|列暗号化キーの暗号化された指定値を暗号化解除するための基本クラス メソッド。 暗号化された値は、指定したキー パスと共に列マスター キーを使用し、指定したアルゴリズムを使用して、暗号化されることが想定されています。|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|指定したキー パスと共に列マスター キーを使用し、指定したアルゴリズムを使用して、列暗号化キーを暗号化するための基本クラス メソッド。|
|パブリックの抽象 void setName (文字列名)|このキー ストア プロバイダーの名前を設定します。|
|パブリックの抽象文字列 getName()|このキー ストア プロバイダーの名前を取得します。|  
  
 新規またはオーバー ロードされたメソッド**SQLServerPreparedStatement**クラス  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|public void setBigDecimal (parameterIndex の int、int 型の精度 x BigDecimal int スケール)<br /><br /> パブリックの void setObject (int parameterIndex、オブジェクトの x、int targetSqlType、整数の精度、int のスケール)<br /><br /> パブリックの void setObject (int parameterIndex、オブジェクトの x、SQLType targetSqlType、整数の精度、スケールの整数)<br /><br /> パブリックの void setTime (int parameterIndex、int スケール x, java.sql.Time)<br /><br /> パブリックの void setTimestamp (int parameterIndex、int スケール x, java.sql.Timestamp) <br />パブリックの void setDateTimeOffset (int parameterIndex, x, int スケール microsoft.sql.DateTimeOffset)|有効桁数またはスケール引数またはその両方の精度を必要とし、スケール情報を特定のデータ型の Always Encrypted をサポートするには、これらのメソッドがオーバー ロードします。|  
|public void setMoney (int parameterIndex、BigDecimal x)<br /><br /> public void setSmallMoney (int parameterIndex、BigDecimal x)<br /><br /> パブリックの void setUniqueIdentifier (int parameterIndex、文字列の guid)<br /><br /> public void setDateTime (int parameterIndex、java.sql.Timestamp x)<br /><br /> public void setSmallDateTime (int parameterIndex、java.sql.Timestamp x)|これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 列にパラメーター値を送信するため既存 setTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド setDateTime() と setSmallDateTime() をそれぞれ使用します。|  
|パブリックの最終的な void setBigDecimal (parameterIndex の int、int 精度 x BigDecimal、スケールの int、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setMoney (int parameterIndex、BigDecimal ブール forceEncrypt x)<br /><br /> パブリックの最終的な void setSmallMoney (int parameterIndex、BigDecimal ブール forceEncrypt x)<br /><br /> パブリックの最終的な void setBoolean (int parameterIndex、ブール型の x、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setByte (int parameterIndex, x, ブール forceEncrypt バイト)<br /><br /> パブリックの最終的な void setBytes (int parameterIndex, バイト x[], ブール forceEncrypt)<br /><br /> パブリックの最終的な void setUniqueIdentifier (int parameterIndex、guid の文字列、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setDouble (int parameterIndex、倍精度浮動小数点 x, ブール forceEncrypt)<br /><br /> パブリックの最終的な void setFloat (int parameterIndex、x を浮動小数点、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setInt (parameterIndex の int、int 型の値、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setLong (int parameterIndex、時間の長い x、ブール forceEncrypt)<br /><br /> パブリックの最終的な setObject (int parameterIndex、オブジェクトの x、int targetSqlType、整数の精度、スケールの int、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setObject (int parameterIndex、オブジェクトの x、SQLType targetSqlType、整数の精度、スケールの整数、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setShort (int parameterIndex、短い x、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setString (int parameterIndex、文字列の str ブール forceEncrypt)<br /><br /> パブリックの最終的な void setNString (int parameterIndex、文字列値、ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTime (int parameterIndex、x を int 型のスケール java.sql.Time ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTimestamp (int parameterIndex、x を int 型のスケール java.sql.Timestamp ブール forceEncrypt)<br /><br /> パブリックの最終的な void setDateTimeOffset (int parameterIndex、x を int スケール、microsoft.sql.DateTimeOffset ブール forceEncrypt)<br /><br /> パブリックの最終的な void setDateTime (int parameterIndex、ブール forceEncrypt x, java.sql.Timestamp)<br /><br /> パブリックの最終的な void setSmallDateTime (int parameterIndex、ブール forceEncrypt x, java.sql.Timestamp)<br /><br /> パブリックの最終的な void setDate (int parameterIndex、x, java.util.Calendar cal、java.sql.Date ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTime (int parameterIndex、x, java.util.Calendar cal、java.sql.Time ブール forceEncrypt)<br /><br /> パブリックの最終的な void setTimestamp (int parameterIndex、x, java.util.Calendar cal、java.sql.Timestamp ブール forceEncrypt)|指定されたパラメーターを、渡された java 値に設定します。<br /><br /> ブール forceEncrypt が設定されている場合は true、クエリにパラメーターが場合にのみ設定の指定の列は暗号化されており、接続またはステートメントでは、Always Encrypted が有効です。<br /><br /> ブール forceEncrypt が false に設定されている場合、ドライバーは、パラメーターで暗号化を強制しません。|  
  
 新規またはオーバー ロードされたメソッド**SQLServerCallableStatement**クラス  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|パブリックの void registerOutParameter (int parameterIndex、sqlType の int、int の有効桁数、int のスケール)<br /><br /> public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)<br /><br /> パブリックの void registerOutParameter (文字列 parameterName、sqlType の int、int の有効桁数、int スケール)<br /><br /> public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)<br />パブリックの void setBigDecimal (文字列 parameterName、BigDecimal bd、int の有効桁数、int のスケール)<br /><br /> パブリックの void setTime (文字列 parameterName, java.sql.Time t, int スケール)<br /><br /> パブリックの void setTimestamp (文字列 parameterName, java.sql.Timestamp t, int スケール)<br /><br /> パブリックの void setDateTimeOffset (文字列 parameterName、microsoft.sql.DateTimeOffset t、int のスケール)<br/><br/>パブリックの最終的な void setObject (文字列 sCol、オブジェクトの x、int targetSqlType、整数の精度、int のスケール)|有効桁数またはスケール引数またはその両方の精度を必要とし、スケール情報を特定のデータ型の Always Encrypted をサポートするには、これらのメソッドがオーバー ロードします。|  
|public void setDateTime (文字列 parameterName, java.sql.Timestamp x)<br /><br /> public void setSmallDateTime (文字列 parameterName, java.sql.Timestamp x)<br /><br /> パブリックの void setUniqueIdentifier (文字列パラメーター名、文字列の guid)<br /><br /> パブリックの void setMoney (文字列 parameterName、BigDecimal bd)<br /><br /> パブリックの void setSmallMoney (文字列 parameterName、BigDecimal bd)<br/><br/>パブリック タイムスタンプ getDateTime (int インデックス)<br/><br/>パブリック タイムスタンプ getDateTime (文字列 sCol)<br/><br/>パブリックのタイムスタンプ getDateTime (int インデックス、予定表の cal)<br/><br/>パブリック タイムスタンプ getSmallDateTime (int インデックス)<br/><br/>パブリック タイムスタンプ getSmallDateTime (文字列 sCol)<br/><br/>パブリックのタイムスタンプ getSmallDateTime (int インデックス、予定表の cal)<br/><br/>パブリックのタイムスタンプ getSmallDateTime (文字列名、予定表の cal)<br/><br/>パブリック BigDecimal getMoney (int インデックス)<br/><br/>パブリック BigDecimal getMoney (文字列 sCol)<br/><br/>パブリック BigDecimal getSmallMoney (int インデックス)<br/><br/>パブリック BigDecimal getSmallMoney (文字列 sCol)|これらのメソッドは、データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime の Always Encrypted をサポートするために追加されます。 <br/><br/>暗号化された datetime2 列にパラメーター値を送信するため既存 setTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド setDateTime() と setSmallDateTime() をそれぞれ使用します。|  
|パブリックの void setObject (文字列パラメーター名、オブジェクト o、int n、m の int、ブール forceEncrypt)<br /><br /> パブリックの void setObject (文字列パラメーター名、オブジェクト obj、SQLType jdbcType、int スケール、ブール forceEncrypt)<br /><br /> public void setDate (文字列 parameterName、予定表 c の場合は、x java.sql.Date ブール forceEncrypt)<br /><br /> パブリックの void setTime (文字列 parameterName, java.sql.Time t、int スケール, ブール forceEncrypt)<br /><br /> public void setTime (文字列 parameterName, x, 予定表 c の場合、java.sql.Time ブール forceEncrypt)<br /><br /> パブリックの void setDateTime (パラメーター名の文字列、ブール forceEncrypt x, java.sql.Timestamp)<br /><br /> パブリックの void setDateTimeOffset (文字列 parameterName、microsoft.sql.DateTimeOffset t、int スケール、ブール forceEncrypt)<br /><br /> パブリックの void setSmallDateTime (パラメーター名の文字列、ブール forceEncrypt x, java.sql.Timestamp)<br /><br /> パブリックの void setTimestamp (文字列 parameterName, java.sql.Timestamp t、int スケール, ブール forceEncrypt)<br /><br /> パブリックの void setTimestamp (パラメーター名の文字列、ブール forceEncrypt x, java.sql.Timestamp)<br /><br /> パブリックの void setUniqueIdentifier (文字列 parameterName、guid の文字列、ブール forceEncrypt)<br /><br /> パブリックの void setBytes (文字列 parameterName, byte b, ブール forceEncrypt)<br /><br /> パブリックの void setByte (文字列 parameterName, バイト b, ブール forceEncrypt)<br /><br /> パブリックの void setString (文字列 parameterName, string, boolean forceEncrypt)<br /><br /> パブリックの最終的な void setNString (文字列パラメーター名、文字列値、ブール forceEncrypt)<br /><br /> パブリックの void setMoney (文字列 parameterName、BigDecimal bd、ブール forceEncrypt)<br /><br /> パブリックの void setSmallMoney (文字列 parameterName、BigDecimal bd、ブール forceEncrypt)<br /><br /> パブリックの void setBigDecimal (文字列 parameterName、BigDecimal bd、int の有効桁数、int スケール、ブール forceEncrypt)<br /><br /> パブリックの void setDouble (文字列 parameterName、ダブル d、ブール forceEncrypt)<br /><br /> パブリックの void setFloat (文字列 parameterName、f を浮動小数点、ブール forceEncrypt)<br /><br /> public void setInt (文字列 parameterName, int i, ブール forceEncrypt)<br /><br /> パブリックの void setLong (文字列 parameterName、時間の長い l、ブール forceEncrypt)<br /><br /> パブリックの void setShort (文字列 parameterName, short s, ブール forceEncrypt)<br /><br /> パブリックの void setBoolean (文字列 parameterNames、b をブール値、ブール forceEncrypt)<br/><br/>public void setTimeStamp (文字列 sCol、予定表 c の場合は、x java.sql.Timestamp ブール forceEncrypt)|指定されたパラメーターを、渡された java 値に設定します。<br /><br /> ブール forceEncrypt が設定されている場合は true、クエリにパラメーターが場合にのみ設定の指定の列は暗号化されており、接続またはステートメントでは、Always Encrypted が有効です。<br /><br /> ブール forceEncrypt が false に設定されている場合、ドライバーは、パラメーターで暗号化を強制しません。|
 

 新規またはオーバー ロードされたメソッド**SQLServerResultSet**クラス  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|パブリック文字列 getUniqueIdentifier (int columnIndex)<br/><br/>パブリック文字列 getUniqueIdentifier (文字列 columnLabel)<br/><br/>   パブリック java.sql.Timestamp getDateTime (int columnIndex) <br/><br/> パブリック java.sql.Timestamp getDateTime (文字列 columnName)   <br/><br/> パブリック java.sql.Timestamp getDateTime (int columnIndex、予定表の cal)   <br/><br/>パブリック java.sql.Timestamp getDateTime (文字列 colName、予定表の cal)    <br/><br/>パブリック java.sql.Timestamp getSmallDateTime (int columnIndex)    <br/><br/> パブリック java.sql.Timestamp getSmallDateTime (文字列 columnName)   <br/><br/> パブリック java.sql.Timestamp getSmallDateTime (int columnIndex、予定表の cal)   <br/><br/> パブリック java.sql.Timestamp getSmallDateTime (文字列 colName、予定表の cal)   <br/><br/>  パブリック BigDecimal getMoney (int columnIndex)  <br/><br/> パブリック BigDecimal getMoney (文字列 columnName)   <br/><br/> パブリック BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  パブリック BigDecimal getSmallMoney (文字列 columnName)  <br/><br/>public void updateMoney (文字列 columnName、BigDecimal x)    <br/><br/>  public void updateSmallMoney (文字列 columnName、BigDecimal x)  <br/><br/>     public void updateDateTime (int インデックス、java.sql.Timestamp x) <br/><br/> public void updateSmallDateTime (int インデックス、java.sql.Timestamp x) |データ型の money、smallmoney、uniqueidentifier、datetime、smalldatetime、Always Encrypted をサポートするために、これらのメソッドが追加されます。 <br/><br/>Datetime2 の暗号化された列を更新するため既存 updateTimestamp() メソッドが使用されることに注意してください。 暗号化された datetime および smalldatetime 列の新しいメソッド updateDateTime() と updateSmallDateTime() をそれぞれ使用します。|
|パブリックの void updateBoolean (int インデックス、ブール型の x、ブール forceEncrypt)  <br/><br/>  パブリックの void updateByte (int index, x, ブール forceEncrypt バイト)  <br/><br/>  パブリックの void updateShort (int インデックス、短い x、ブール forceEncrypt)  <br/><br/> パブリックの void updateInt (int インデックス、int、ブール forceEncrypt x)   <br/><br/>  パブリックの void updateLong (int インデックス、時間の長い x、ブール forceEncrypt)  <br/><br/> パブリックの void updateFloat (int インデックス、x を浮動小数点、ブール forceEncrypt)   <br/><br/> パブリックの void updateDouble (int index, double x, ブール forceEncrypt)   <br/><br/> public void updateMoney (int index, x, ブール forceEncrypt BigDecimal)   <br/><br/>  public void updateMoney (文字列 columnName、BigDecimal ブール forceEncrypt x)  <br/><br/> public void updateSmallMoney (int index, x, ブール forceEncrypt BigDecimal)   <br/><br/>  public void updateSmallMoney (文字列 columnName、BigDecimal ブール forceEncrypt x)  <br/><br/> パブリックの void updateBigDecimal (int インデックス、整数の精度 x BigDecimal、スケールの整数、ブール forceEncrypt)   <br/><br/>  パブリックの void updateString (int columnIndex、文字列の文字列値、ブール forceEncrypt)  <br/><br/>  パブリックの void updateNString (int columnIndex、文字列の文字列、ブール forceEncrypt)  <br/><br/>  パブリックの void updateNString (文字列 columnLabel、文字列の文字列、ブール forceEncrypt)  <br/><br/> パブリックの void updateBytes (int インデックス, バイト x[], ブール forceEncrypt)   <br/><br/>  パブリックの void updateDate (int index, java.sql.Date ブール forceEncrypt x)  <br/><br/> public void updateTime (int インデックス、x は、整数のスケール java.sql.Time ブール forceEncrypt)   <br/><br/> public void updateTimestamp (int インデックス、x を int 型のスケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/> public void updateDateTime (int インデックス、x は、整数のスケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/> public void updateSmallDateTime (int インデックス、x は、整数のスケール java.sql.Timestamp ブール forceEncrypt)   <br/><br/>  public void updateDateTimeOffset (int インデックス、x は、整数のスケール、microsoft.sql.DateTimeOffset ブール forceEncrypt)  <br/><br/> public void updateUniqueIdentifier (int インデックス、文字列、ブール forceEncrypt x)    <br/><br/>  パブリックの void updateObject (int インデックス、オブジェクトの x、int の有効桁数、スケールの int、ブール forceEncrypt)  <br/><br/>  パブリックの void updateObject (int インデックス, オブジェクト obj、SQLType targetSqlType、int スケール, ブール forceEncrypt)  <br/><br/> パブリックの void updateBoolean (columnName の文字列、ブール型の x、ブール forceEncrypt)    <br/><br/>  パブリックの void updateByte (columnName の文字列、ブール forceEncrypt x バイト)  <br/><br/>  パブリックの void updateShort (文字列 columnName、短い x、ブール forceEncrypt)  <br/><br/> パブリックの void updateInt (columnName の文字列、int、ブール forceEncrypt x)   <br/><br/>   パブリックの void updateLong (文字列 columnName、時間の長い x、ブール forceEncrypt) <br/><br/>  パブリックの void updateFloat (文字列 columnName、x を浮動小数点、ブール forceEncrypt)  <br/><br/>  パブリックの void updateDouble (文字列 columnName、倍精度浮動小数点 x, ブール forceEncrypt)  <br/><br/> public void updateBigDecimal (文字列 columnName、BigDecimal ブール forceEncrypt x)   <br/><br/>  パブリックの void updateBigDecimal (columnName の文字列、整数の精度 x BigDecimal、スケールの整数、ブール forceEncrypt)  <br/><br/> public void updateString (文字列 columnName、文字列、ブール forceEncrypt x)   <br/><br/>  パブリックの void updateBytes (columnName の文字列、バイト x[]、ブール forceEncrypt)  <br/><br/> パブリックの void updateDate (columnName の文字列、ブール forceEncrypt x, java.sql.Date)   <br/><br/>  public void updateTime (文字列 columnName, x, int スケールの場合、java.sql.Time ブール forceEncrypt)  <br/><br/>  public void updateTimestamp (文字列 columnName, x, int スケール、java.sql.Timestamp ブール forceEncrypt)  <br/><br/> public void updateDateTime (文字列 columnName, x, int スケール、java.sql.Timestamp ブール forceEncrypt)   <br/><br/>  public void updateSmallDateTime (文字列 columnName, x, int スケール、java.sql.Timestamp ブール forceEncrypt)  <br/><br/>  public void updateDateTimeOffset (文字列 columnName、x を int スケール、microsoft.sql.DateTimeOffset ブール forceEncrypt)  <br/><br/>  public void updateUniqueIdentifier (文字列 columnName、文字列、ブール forceEncrypt x)<br/><br/>パブリックの void updateObject (文字列 columnName、オブジェクトの x、int の有効桁数、スケールの int、ブール forceEncrypt)<br/><br/>パブリックの void updateObject (文字列 columnName、オブジェクト obj、SQLType targetSqlType、スケールの int、ブール forceEncrypt)|指定された java 値に指定された列を更新します。<br/><br/>ブール forceEncrypt に設定されている場合は true、列にのみ設定されますが暗号化されていて、接続またはステートメントでは、Always Encrypted が有効です。<br/><br/>ブール forceEncrypt が false に設定されている場合、ドライバーは、パラメーターで暗号化を強制しません。|

  
新しい種類**microsoft.sql.Types**クラス
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|DATETIME、SMALLDATETIME、MONEY、SMALLMONEY、GUID|対象の SQL 型としてこれらの型を使用するパラメーターの値を送信するときに**暗号化**datetime、smalldatetime、money、smallmoney、setObject()/updateObject() API メソッドを使用して uniqueidentifier 列。|  
  
  
 **SQLServerStatementColumnEncryptionSetting 列挙型**  
  
 暗号化された列を読み書きするときにデータを送受信する方法を指定します。 クエリによっては、暗号化されていない列を使用する場合に Always Encrypted ドライバーの処理をバイパスすることにより、パフォーマンスの影響が軽減される可能性があります。 暗号化を回避したり、プレーンテキスト データにアクセスしたりするためにこれらの設定値を使用することはできません。  
  
 **構文**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **メンバー**  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|UseConnectionSetting|接続文字列で、コマンドが Always Encrypted 設定を既定として設定するように指定します。|  
|有効|クエリで Always Encrypted を有効にします。|  
|ResultSetOnly|ドライバーでコマンドの結果だけを Always Encrypted ルーチンで処理するよう指定します。 コマンドに暗号化が必要なパラメーターがない場合にこの値を使用します。|  
|Disabled|クエリで Always Encrypted を無効にします。|  
  
 AE のステートメント レベルの設定は、SQLServerConnection クラスと SQLServerConnectionPoolProxy クラスに追加されます。 新しい設定では、これらのクラスに次のメソッドがオーバー ロードします。  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|パブリック ステートメント createStatement (int %n タイプ、nConcur の int、int statementHoldability、SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|特定の種類、同時実行、保持機能、および列の暗号化設定を持つ結果セット オブジェクトを生成するステートメント オブジェクトを作成します。|  
|パブリックの CallableStatement prepareCall (文字列 sql, %n タイプの int、int nConcur、int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|特定の種類、同時実行性、および保持機能を持つ結果セット オブジェクトを生成する特定の列暗号化設定で CallableStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (文字列 sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|自動生成キーを取得する機能を持つ指定された列暗号化設定で PreparedStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (sql の文字列, 文字列 columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|特定の列名を持つオブジェクトを結果セットを生成する特定の列暗号化設定で PreparedStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (の sql の文字列、int [columnIndexes、SQLServerStatementColumnEncryptionSetting stmtColEncSetting|指定した列のインデックスを持つオブジェクトを結果セットを生成する特定の列暗号化設定で PreparedStatement オブジェクトを作成します。|  
|パブリックの PreparedStatement prepareStatement (文字列 sql, %n タイプの int、int nConcur、int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|特定の種類、同時実行性、および保持機能を持つ結果セット オブジェクトを生成する特定の列暗号化設定には、PreparedStatement オブジェクトを作成します。|  
  
> [!NOTE]  
>  クエリの Always Encrypted が無効になっているし、クエリがパラメーターである暗号化された (暗号化された列に対応する) 必要があるパラメーターには、クエリは失敗します。  
>   
>  クエリの Always Encrypted が無効になっているクエリは、暗号化された列から結果を返す場合は、クエリは暗号化された値を返します。 暗号化された値は、varbinary データ型になります。  
  
 ## <a name="see-also"></a>参照  
 [JDBC ドライバーで Always Encrypted を使用する](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

