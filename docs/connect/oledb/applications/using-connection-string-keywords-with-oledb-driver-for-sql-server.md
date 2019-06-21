---
title: OLE DB Driver for SQL Server での接続文字列キーワードの使用 | Microsoft Docs
description: OLE DB Driver for SQL Server での接続文字列キーワードの使用
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 91e498a1db30df380d7f2009f0fe34a9b4541467
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778031"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server での接続文字列キーワードの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  一部 OLE DB Driver for SQL Server Api では、接続文字列を使用して、接続属性を指定します。 接続文字列はキーワードとそれに関連する値のリストです。各キーワードによって特定の接続属性を識別します。  
  
> [!NOTE]
> OLE DB Driver for SQL Server では、旧バージョンとの互換性を維持するために接続文字列のあいまいさが許可されます (たとえば、キーワードを複数回指定したり、位置や優先順位に基づいた解決方法を使用して、競合するキーワードを指定したりすることができます)。 OLE DB Driver for SQL Server の今後のリリースは、接続文字列のあいまいさを許可しない場合があります。 OLE DB Driver for SQL Server を使用するアプリケーションでは、あいまいな接続文字列を利用しないように変更することをお勧めします。  
  
 次のセクションでは、キーワードを併用して OLE DB Driver for SQL Server、および ActiveX Data Objects (ADO) for SQL Server データ プロバイダーとして OLE DB ドライバーを使用する場合について説明します。  

  
## <a name="ole-db-driver-connection-string-keywords"></a>OLE DB ドライバー接続文字列キーワード  
 OLE DB アプリケーションでデータ ソース オブジェクトを初期化する方法は 2 つあります。  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 最初の方法では、DBPROPSET_DBINIT プロパティ セットのプロパティ DBPROP_INIT_PROVIDERSTRING を設定することにより、プロバイダー文字列で接続プロパティを初期化できます。 2 番目の方法では、**IDataInitialize::GetDataSource** メソッドに初期化文字列を渡して、接続プロパティを初期化できます。 いずれの方法でも同一の OLE DB 接続プロパティが初期化されますが、使用されるキーワードのセットは異なります。 **IDataInitialize::GetDataSource** で使用されるキーワードのセットには、少なくとも初期化プロパティ グループ内のプロパティの説明が含まれます。  
  
 対応する OLE DB プロパティを持つプロバイダー文字列の設定は一部の既定値に設定されるか、値に明示的に設定され、OLE DB プロパティ値はプロバイダー文字列の設定をオーバーライドします。  
  
 DBPROP_INIT_PROVIDERSTRING 値によってプロバイダー文字列内で設定されるブール型のプロパティは、値 "yes" と "no" を使用して設定します。 **IDataInitialize::GetDataSource** によって初期化文字列内で設定されるブール型のプロパティは、値 "true" と "false" を使用して設定します。  
  
 **IDataInitialize::GetDataSource** を使用するアプリケーションでは、既定値を持たないプロパティに対してのみ、**IDBInitialize::Initialize** で用いられるキーワードも利用できます。 **IDataInitialize::GetDataSource** キーワードと **IDBInitialize::Initialize** キーワードの両方を初期化文字列で使用すると、**IDataInitialize::GetDataSource** キーワードの設定が利用されます。 今後のリリースではこの動作が維持されない可能性があるので、**IDataInitialize:GetDataSource** 接続文字列では **IDBInitialize::Initialize** キーワードを使用しないことを強くお勧めします。  
  
> [!NOTE]  
>  **IDataInitialize::GetDataSource** を介して渡される接続文字列は、プロパティに変換され、**IDBProperties::SetProperties** で適用されます。 コンポーネント サービスによって **IDBProperties::GetPropertyInfo** でプロパティ説明が検出された場合、このプロパティはスタンドアロンのプロパティとして適用されます。 それ以外の場合は、DBPROP_PROVIDERSTRING プロパティを介して適用されます。 たとえば、接続文字列を指定する**データ ソース = server1;Server = server2**、**データ ソース**をプロパティとして設定されますが、 **Server**プロバイダー文字列に変わります。  
  
 同じプロバイダー固有のプロパティのインスタンスを複数指定した場合、最初のプロパティの最初の値が使用されます。  
  
 **IDBInitialize::Initialize** と共に DBPROP_INIT_PROVIDERSTRING を利用する OLE DB アプリケーションで使用される接続文字列の構文は次のとおりです。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて中かっこで囲むことができます。常に中かっこを使用すると、 属性値に英数字以外の文字が含まれる場合の問題を回避できます。 最初の右中かっこが値の終わりと見なされるため、値に右中かっこを含めることはできません。  
  
 接続文字列キーワードの等号 (=) の後のスペース文字は、値を引用符で囲んだ場合でも、リテラルとして解釈されます。  
  
 次の表に、DBPROP_INIT_PROVIDERSTRING と共に使用できるキーワードを示します。  
  
|Keyword|初期化プロパティ|[説明]|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|"Address" のシノニム。|  
|**Address**|SSPROP_INIT_NETWORKADDRESS|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスを実行しているサーバーのネットワーク アドレス。 **Address** は、通常、サーバーのネットワーク名ですが、パイプ、IP アドレス、または TCP/IP ポートとソケット アドレスなど、他の名前を指定してもかまいません。<br /><br /> IP アドレスを指定する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで TCP/IP または名前付きパイプ プロトコルが有効になっていることを確認します。<br /><br /> 値**アドレス**に渡される値よりも優先**Server** for SQL Server OLE DB ドライバーを使用する場合、接続文字列にします。 `Address=;` の場合は、**Server** キーワードで指定されているサーバーに接続されますが、`Address= ;, Address=.;`、`Address=localhost;`、および `Address=(local);` の場合はすべて、ローカル サーバーに接続されることにも注意してください。<br /><br /> **Address** キーワードの完全な構文は次のとおりです。<br /><br /> [_プロトコル_ **:** ]_アドレス_[ **、** _ポート&#124;\pipe\pipename_]<br /><br /> _protocol_ には、 **tcp** (TCP/IP)、 **lpc** (共有メモリ)、または **np** (名前付きパイプ) を指定できます。 プロトコルの詳細については、次を参照してください。 [Configure Client Protocols](../../../database-engine/configure-windows/configure-client-protocols.md)します。<br /><br /> どちらの場合_プロトコル_も**ネットワーク**キーワードを指定すると、OLE DB Driver for SQL Server がで指定されたプロトコルの順序を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager。<br /><br /> *port* は、指定したサーバー上の接続先のポートです。 既定では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はポート 1433 を使用します。|   
|**APP**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 有効値は、**ReadOnly** と **ReadWrite** です。<br /><br /> 既定値は**ReadWrite**します。 詳細について OLE DB Driver for SQL Server のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL Server で高可用性、ディザスター リカバリーのためサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 **AttachDBFileName** を使用するには、プロバイダー文字列の Database キーワードでデータベース名を指定する必要もあります。 データベースが以前にアタッチされていた場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] により再アタッチされることはありません (アタッチされたデータベースがその接続の既定のデータベースとして使用されます)。|  
|**認証**<a href="#table1_1"><sup id="table1_authmode">**1**</sup></a>|SSPROP_AUTH_MODE|使用される SQL または Active Directory 認証を指定します。 有効な値は、<br/><ul><li>`(not set)`。 その他のキーワードによって決定されます認証モードです。</li><li>`ActiveDirectoryPassword:` Active Directory の認証ログイン ID とパスワードを使用します。</li><li>`ActiveDirectoryIntegrated:` 現在のログイン ユーザーの Windows アカウントの資格情報を使用して Active Directory に統合認証です。</li><br/>**注:** が**推奨**を使用してそのアプリケーション`Integrated Security`(または`Trusted_Connection`) 認証に関するキーワードまたは対応するプロパティの値を設定、`Authentication`キーワード (またはその対応するプロパティ) を`ActiveDirectoryIntegrated`新しい暗号化と証明書の検証動作を有効にします。<br/><br/><li>`SqlPassword:` 認証ログイン ID とパスワードを使用します。</li><br/>**注:** が**推奨**を使用してそのアプリケーション`SQL Server`認証設定の値、`Authentication`キーワード (またはその対応するプロパティ) を`SqlPassword`新しい暗号化を有効にし、証明書の検証動作。</ul>|
|**自動変換します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "yes" と "no" です。|  
|**[データベース]**|DBPROP_INIT_CATALOG|データベース名です。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|データ型を使用する処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および SQL Server 2000 データ型を示す "80" です。|  
|**暗号化**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server の既定のプロバイダーで生成された SPN を使用するとします。|  
|**言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語。|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のサーバーの場合)。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可用性グループまたは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **MultiSubnetFailover=Yes** を指定してください。 **MultiSubnetFailover=Yes** の場合、(現在) アクティブなサーバーをより迅速に検出し、接続するように OLE DB Driver for SQL Server が構成されます。 可能な値は、 **[はい]** と **[いいえ]** です。 既定値は **No** です。 例:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> 詳細について OLE DB Driver for SQL Server のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL Server で高可用性、ディザスター リカバリーのためサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|"Network" のシノニム。|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|"Network" のシノニム。|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "yes" と "no" を値として受け取ります。 "no" の場合、データ ソース オブジェクトには機密の認証情報を保存できません。|  
|**PWD**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**[サーバー]**|DBPROP_INIT_DATASOURCE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前。 ネットワーク上のサーバーの名前、IP アドレス、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーの別名を指定する必要があります。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> **アドレス**キーワードよりも優先、 **Server**キーワード。<br /><br /> 次のいずれかを指定することで、ローカル サーバー上の既定のインスタンスに接続できます。<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** *instancename* **;**<br /><br /> LocalDB のサポートの詳細については、次を参照してください。 [OLE DB Driver for SQL Server で LocalDB のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)します。<br /><br /> 名前付きインスタンスを指定する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、追加 **\\** _InstanceName_します。<br /><br /> サーバーを指定しなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続されます。<br /><br /> IP アドレスを指定する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで TCP/IP または名前付きパイプ プロトコルが有効になっていることを確認します。<br /><br /> **Server** キーワードの完全な構文は次のとおりです。<br /><br /> **Server=** ["_プロトコル_" **:** ]"*サーバー*"[ **,** "_ポート_"]<br /><br /> _protocol_ には、 **tcp** (TCP/IP)、 **lpc** (共有メモリ)、または **np** (名前付きパイプ) を指定できます。<br /><br /> 名前付きパイプを指定する例を次に示します。<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> この行では、名前付きパイプのプロトコル、ローカル コンピューター上の名前付きパイプ (`\\.\pipe`)、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前 (`MSSQL$MYINST01`)、および名前付きパイプの既定の名前 (`sql/query`) を指定しています。<br /><br /> どちらの場合、*プロトコル*も**ネットワーク**キーワードを指定すると、OLE DB Driver for SQL Server がで指定されたプロトコルの順序を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager。<br /><br /> *port* は、指定したサーバー上の接続先のポートです。 既定では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はポート 1433 を使用します。<br /><br /> 渡される値の先頭のスペースは無視されます**Server** for SQL Server OLE DB ドライバーを使用する場合、接続文字列にします。|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server の既定のプロバイダーで生成された SPN を使用するとします。|  
|**Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|ときに、OLE DB Driver for SQL Server ログインの検証に Windows 認証モードを使用するを"yes"のように指示します。 それ以外の場合は、OLE DB Driver for SQL Server に対して、ログイン検証で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のユーザー名とパスワードを使用するように指示し、UID キーワードと PWD キーワードの指定が必要になります。|  
|**TrustServerCertificate**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "yes" と "no" を値として受け取ります。 既定値は "no" です。これはサーバー証明書が検証されることを示します。|  
|**UID**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] およびそれ以降に接続する場合のメタデータの取得方法を制御します。 有効値は、"yes" および "no" です。 既定値は "no" です。<br /><br />既定で、OLE DB Driver for SQL Server を使用して[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)と[sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)ストアド プロシージャのメタデータを取得します。 これらのストアド プロシージャにいくつかの制限があります (例: が失敗した一時テーブル上で動作している場合)。 設定**UseFMTONLY**を"yes"を使用して、ドライバーに指示[SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md)メタデータの取得の代わりにします。|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|このキーワードは非推奨し、SQL Server OLE DB ドライバーによってその設定は無視されます。|  
|**WSID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
<b id="table1_1">[1]: </b> /認証アクセス トークンの初期化プロパティまたは対応する接続文字列キーワードを使用してセキュリティを強化する暗号化と証明書の検証動作が変更されました。 詳細については、次を参照してください。[暗号化と証明書の検証](../features/using-azure-active-directory.md#encryption-and-certificate-validation)です。

 **IDataInitialize::GetDataSource** を利用する OLE DB アプリケーションで使用される接続文字列の構文は次のとおりです。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 プロパティの使用方法は、プロパティのスコープで許可される構文に従っている必要があります。  たとえば、 **WSID**中かっこを使用して ( **{}** ) 引用符文字と**アプリケーション名**では一重 ( **'** ) またはdouble ( **"** ) 引用符文字。 引用符で囲むことができるのは、文字列のプロパティのみです。 整数または列挙のプロパティを引用符で囲むと、"接続文字列は OLE DB 仕様に準拠していません" というエラーが発生します。  
  
 属性値は必要に応じて一重引用符または二重引用符で囲むことができます。常にこれらの引用符を使用すると、 値に英数字以外の文字が含まれる場合の問題を回避できます。 二重引用符の場合は、値の中に含めることもできます。  
  
 接続文字列キーワードの等号 (=) の後のスペース文字は、値を引用符で囲んだ場合でも、リテラルとして解釈されます。  
  
 接続文字列に次の表のプロパティが複数含まれている場合は、最後のプロパティの値が使用されます。  
  
 次の表では、**IDataInitialize::GetDataSource** と共に使用できるキーワードについて説明します。  
  
|Keyword|初期化プロパティ|[説明]|  
|-------------|-----------------------------|-----------------|  
|**Access Token**<a href="#table2_1"><sup id="table2_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|アクセス トークンは、Azure Active Directory に対して認証するために使用します。 <br/><br/>**注:** このキーワードを指定するとエラーにはまた`UID`、 `PWD`、 `Trusted_Connection`、または`Authentication`接続文字列キーワードまたは対応するプロパティ/キーワード。|
|**Application Name**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 有効値は、**ReadOnly** と **ReadWrite** です。<br /><br /> 既定値は**ReadWrite**します。 詳細について OLE DB Driver for SQL Server のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL Server で高可用性、ディザスター リカバリーのためサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|  
|**認証**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|使用される SQL または Active Directory 認証を指定します。 有効な値は、<br/><ul><li>`(not set)`。 その他のキーワードによって決定されます認証モードです。</li><li>`ActiveDirectoryPassword:` Active Directory の認証ログイン ID とパスワードを使用します。</li><li>`ActiveDirectoryIntegrated:` 現在のログイン ユーザーの Windows アカウントの資格情報を使用して Active Directory に統合認証です。</li><br/>**注:** が**推奨**を使用してそのアプリケーション`Integrated Security`(または`Trusted_Connection`) 認証に関するキーワードまたは対応するプロパティの値を設定、`Authentication`キーワード (またはその対応するプロパティ) を`ActiveDirectoryIntegrated`新しい暗号化と証明書の検証動作を有効にします。<br/><br/><li>`SqlPassword:` 認証ログイン ID とパスワードを使用します。</li><br/>**注:** が**推奨**を使用してそのアプリケーション`SQL Server`認証設定の値、`Authentication`キーワード (またはその対応するプロパティ) を`SqlPassword`新しい暗号化を有効にし、証明書の検証動作。</ul>|
|**自動変換します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "true" と "false" です。|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前。|  
|**[データ ソース]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、このトピックの **Server** キーワードに関する説明を参照してください。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|データ型を使用する処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] データ型を示す "80" です。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server の既定のプロバイダーで生成された SPN を使用するとします。|  
|**初期カタログ**|DBPROP_INIT_CATALOG|データベース名です。|  
|**初期ファイル名**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 **AttachDBFileName** を使用するには、プロバイダー文字列の DATABASE キーワードでデータベース名を指定する必要もあります。 データベースが以前にアタッチされていた場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] により再アタッチされることはありません (アタッチされたデータベースがその接続の既定のデータベースとして使用されます)。|  
|**統合セキュリティ**|DBPROP_AUTH_INTEGRATED|Windows 認証の値 "SSPI" を受け取ります。|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします。 認識できる値は "true" と "false" です。 既定値は "false" です。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可用性グループまたは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **MultiSubnetFailover=True** を指定してください。 **MultiSubnetFailover=True** の場合、(現在) アクティブなサーバーをより迅速に検出し、接続するように OLE DB Driver for SQL Server が構成されます。 指定できる値は、 **[True]** および **[False]** です。 既定値は **False**です。 例:<br /><br /> `MultiSubnetFailover=True`<br /><br /> 詳細について OLE DB Driver for SQL Server のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL Server で高可用性、ディザスター リカバリーのためサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、このトピックの **Address** キーワードに関する説明を参照してください。|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**パスワード**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "true" と "false" を値として受け取ります。 "false" の場合、データ ソース オブジェクトには機密の認証情報を保存できません|  
|**プロバイダー**||OLE DB driver for SQL Server、"MSOLEDBSQL"があります。|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server の既定のプロバイダーで生成された SPN を使用するとします。|  
|**Trust Server Certificate**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "true" と "false" を値として受け取ります。 既定値は "false" です。これはサーバー証明書が検証されることを示します。|  
|**Use Encryption for Data**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 指定できる値は "true" と "false" です。 既定値は "false" です。|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] およびそれ以降に接続する場合のメタデータの取得方法を制御します。 指定できる値は "true" と "false" です。 既定値は "false" です。<br /><br />既定で、OLE DB Driver for SQL Server を使用して[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)と[sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)ストアド プロシージャのメタデータを取得します。 これらのストアド プロシージャにいくつかの制限があります (例: が失敗した一時テーブル上で動作している場合)。 設定**FMTONLY の使用**"true"を使用して、ドライバーに指示する[SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md)メタデータの取得の代わりにします。|  
|**[ユーザー ID]**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**Workstation ID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
<b id="table2_1">[1]: </b> /認証アクセス トークンの初期化プロパティまたは対応する接続文字列キーワードを使用してセキュリティを強化する暗号化と証明書の検証動作が変更されました。 詳細については、次を参照してください。[暗号化と証明書の検証](../features/using-azure-active-directory.md#encryption-and-certificate-validation)です。

 **注** 接続文字列の "Old Password" プロパティは SSPROP_AUTH_OLD_PASSWORD に設定され、現在の (または期限切れの) パスワードが設定されます。このパスワードをプロバイダー文字列のプロパティ経由で使用することはできません。  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>ADO (ActiveX Data Objects) の接続文字列のキーワード  
 ADO アプリケーションでは、**ADODBConnection** オブジェクトの **ConnectionString** プロパティが設定されるか、**ADODBConnection** オブジェクトの **Open** メソッドにパラメーターとして接続文字列が指定されます。  
  
 また、ADO アプリケーションでは、既定値がないプロパティにのみ、OLE DB **IDBInitialize::Initialize** メソッドで使用されるキーワードを利用できます。 アプリケーションにより、初期化文字列で ADO キーワードと **IDBInitialize::Initialize** キーワードが両方とも使われている場合、ADO キーワードの設定が使用されます。 アプリケーションでは ADO 接続文字列のキーワードのみを使用することを強くお勧めします。  
  
 ADO で使用される接続文字列の構文を次に示します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて二重引用符で囲むことができます。常に二重引用符を使用すると、 値に英数字以外の文字が含まれる場合の問題を回避できます。 属性値に二重引用符を含めることはできません。  
  
 次の表に、ADO 接続文字列と共に使用できるキーワードを示します。  
  
|Keyword|初期化プロパティ|[説明]|  
|-------------|-----------------------------|-----------------|  
|**Access Token**<a href="#table3_1"><sup id="table3_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|アクセス トークンは、Azure Active Directory に対して認証するために使用します。<br/><br/>**注:** このキーワードを指定するとエラーにはまた`UID`、 `PWD`、 `Trusted_Connection`、または`Authentication`接続文字列キーワードまたは対応するプロパティ/キーワード。|
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 有効値は、**ReadOnly** と **ReadWrite** です。<br /><br /> 既定値は**ReadWrite**します。 詳細について OLE DB Driver for SQL Server のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL Server で高可用性、ディザスター リカバリーのためサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|  
|**Application Name**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**認証**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|使用される SQL または Active Directory 認証を指定します。 有効な値は、<br/><ul><li>`(not set)`。 その他のキーワードによって決定されます認証モードです。</li><li>`ActiveDirectoryPassword:` Active Directory の認証ログイン ID とパスワードを使用します。</li><li>`ActiveDirectoryIntegrated:` 現在のログイン ユーザーの Windows アカウントの資格情報を使用して Active Directory に統合認証です。</li><br/>**注:** が**推奨**を使用してそのアプリケーション`Integrated Security`(または`Trusted_Connection`) 認証に関するキーワードまたは対応するプロパティの値を設定、`Authentication`キーワード (またはその対応するプロパティ) を`ActiveDirectoryIntegrated`新しい暗号化と証明書の検証動作を有効にします。<br/><br/><li>`SqlPassword:` 認証ログイン ID とパスワードを使用します。</li><br/>**注:** が**推奨**を使用してそのアプリケーション`SQL Server`認証設定の値、`Authentication`キーワード (またはその対応するプロパティ) を`SqlPassword`新しい暗号化を有効にし、証明書の検証動作。</ul>|
|**自動変換します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "true" と "false" です。|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前。|  
|**[データ ソース]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、このトピックの **Server** キーワードに関する説明を参照してください。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|使用するデータ型処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および SQL Server 2000 データ型を示す "80" です。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server の既定のプロバイダーで生成された SPN を使用するとします。|  
|**初期カタログ**|DBPROP_INIT_CATALOG|データベース名です。|  
|**初期ファイル名**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 **AttachDBFileName** を使用するには、プロバイダー文字列の DATABASE キーワードでデータベース名を指定する必要もあります。 データベースが以前にアタッチされていた場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] により再アタッチされることはありません (アタッチされたデータベースがその接続の既定のデータベースとして使用されます)。|  
|**統合セキュリティ**|DBPROP_AUTH_INTEGRATED|Windows 認証の値 "SSPI" を受け取ります。|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のサーバーの場合)。 認識できる値は "true" と "false" です。既定値は "false" です。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可用性グループまたは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **MultiSubnetFailover=True** を指定してください。 **MultiSubnetFailover=True** の場合、(現在) アクティブなサーバーをより迅速に検出し、接続するように OLE DB Driver for SQL Server が構成されます。 指定できる値は、 **[True]** および **[False]** です。 既定値は **False**です。 例:<br /><br /> `MultiSubnetFailover=True`<br /><br /> 詳細について OLE DB Driver for SQL Server のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL Server で高可用性、ディザスター リカバリーのためサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、このトピックの **Address** キーワードに関する説明を参照してください。|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**パスワード**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "true" と "false" を値として受け取ります。 "false" の場合、データ ソース オブジェクトには機密の認証情報を保存できません。|  
|**プロバイダー**||OLE DB driver for SQL Server、"MSOLEDBSQL"があります。|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server の既定のプロバイダーで生成された SPN を使用するとします。|  
|**Trust Server Certificate**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "true" と "false" を値として受け取ります。 既定値は "false" です。これはサーバー証明書が検証されることを示します。|  
|**Use Encryption for Data**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 指定できる値は "true" と "false" です。 既定値は "false" です。|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] およびそれ以降に接続する場合のメタデータの取得方法を制御します。 指定できる値は "true" と "false" です。 既定値は "false" です。<br /><br />既定で、OLE DB Driver for SQL Server を使用して[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)と[sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)ストアド プロシージャのメタデータを取得します。 これらのストアド プロシージャにいくつかの制限があります (例: が失敗した一時テーブル上で動作している場合)。 設定**FMTONLY の使用**"true"を使用して、ドライバーに指示する[SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md)メタデータの取得の代わりにします。|  
|**[ユーザー ID]**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**Workstation ID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
<b id="table3_1">[1]: </b> /認証アクセス トークンの初期化プロパティまたは対応する接続文字列キーワードを使用してセキュリティを強化する暗号化と証明書の検証動作が変更されました。 詳細については、次を参照してください。[暗号化と証明書の検証](../features/using-azure-active-directory.md#encryption-and-certificate-validation)です。

 **注** 接続文字列の "Old Password" プロパティは SSPROP_AUTH_OLD_PASSWORD に設定され、現在の (または期限切れの) パスワードが設定されます。このパスワードをプロバイダー文字列のプロパティ経由で使用することはできません。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
