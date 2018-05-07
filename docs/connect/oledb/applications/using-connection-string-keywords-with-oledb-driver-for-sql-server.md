---
title: SQL Server の OLE DB ドライバーとの接続文字列キーワードを使用して |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーで接続文字列キーワードを使用します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a88e1ba37c1c5ddab0af1bbba411a08429fd2a05
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB ドライバーとの接続文字列キーワードを使用してください。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  一部 OLE DB Driver for SQL Server Api では、接続文字列を使用して、接続属性を指定します。 接続文字列はキーワードとそれに関連する値のリストです。各キーワードによって特定の接続属性を識別します。  
  
> **注:** 旧バージョンとの互換性を維持する接続文字列のあいまいさにより、OLE DB Driver for SQL Server (たとえば、いくつかのキーワードを複数回指定することがあります、位置に基づいて解像度で競合するキーワードを許可することがありますか優先順位)。 OLE DB Driver for SQL Server の今後のリリースは、接続文字列のあいまいさを許可しない場合があります。 接続文字列のあいまいさの依存を排除する OLE DB Driver for SQL Server を使用するアプリケーションを変更する場合は、ことをお勧めを勧めします。  
  
 次のセクションでは、使用できる OLE DB ドライバーで SQL Server、および ActiveX データ オブジェクト (ADO) のデータ プロバイダーとして、SQL Server の OLE DB Driver を使用する場合のキーワードについて説明します。  

  
## <a name="ole-db-driver-connection-string-keywords"></a>OLE DB ドライバー接続文字列キーワード  
 OLE DB アプリケーションでデータ ソース オブジェクトを初期化する方法は 2 つあります。  
  
-   **Idbinitialize::initialize**  
  
-   **Idatainitialize::getdatasource**  
  
 最初の方法では、DBPROPSET_DBINIT プロパティ セットのプロパティ DBPROP_INIT_PROVIDERSTRING を設定することにより、プロバイダー文字列で接続プロパティを初期化できます。 2 番目のケースでは、初期化文字列に渡せる**idatainitialize::getdatasource**接続のプロパティを初期化します。 いずれの方法でも同一の OLE DB 接続プロパティが初期化されますが、使用されるキーワードのセットは異なります。 使用されるキーワードのセット**idatainitialize::getdatasource**が最小 initialization プロパティ グループ内のプロパティの説明。  
  
 対応する OLE DB プロパティを持つプロバイダー文字列の設定は一部の既定値に設定されるか、値に明示的に設定され、OLE DB プロパティ値はプロバイダー文字列の設定をオーバーライドします。  
  
 DBPROP_INIT_PROVIDERSTRING 値によってプロバイダー文字列内で設定されるブール型のプロパティは、値 "yes" と "no" を使用して設定します。 使用して初期化文字列に設定するブール型プロパティ**idatainitialize::getdatasource**値"true"および"false"を使用して設定されます。  
  
 使用してアプリケーション**idatainitialize::getdatasource**で使用されるキーワードを使用することも**idbinitialize::initialize**が既定値を持たないプロパティに対してのみです。 アプリケーションでは、どちらも使用している場合、 **idatainitialize::getdatasource**キーワードおよび**idbinitialize::initialize**初期化文字列のキーワードで、 **idatainitialize::getdatasource**キーワードの設定を使用します。 アプリケーションが使用しないことを強くお勧め**idbinitialize::initialize**キーワード**IDataInitialize:GetDataSource**接続文字列をこの動作が維持されない将来のリリースとします。  
  
> [!NOTE]  
>  接続文字列を通過**idatainitialize::getdatasource**プロパティに変換され、使用して適用**idbproperties::setproperties**です。 コンポーネント サービスのプロパティの説明が見つかった場合 **:getpropertyinfo**、このプロパティはスタンドアロン プロパティとして適用されます。 それ以外の場合は、DBPROP_PROVIDERSTRING プロパティを介して適用されます。 たとえば、接続文字列を指定する**データ ソース = server1 です。Server = server2**、**データ ソース**をプロパティとして設定されますが、**サーバー**プロバイダー文字列に変わります。  
  
 同じプロバイダー固有のプロパティの複数のインスタンスを指定する場合、最初のプロパティの最初の値が使用されます。  
  
 と共に DBPROP_INIT_PROVIDERSTRING を使用して OLE DB アプリケーションで使用される接続文字列**idbinitialize::initialize**次の構文します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて中かっこで囲むことができます。常に中かっこを使用すると、 属性値に英数字以外の文字が含まれる場合の問題を回避できます。 最初の右中かっこが値の終わりと見なされるため、値に右中かっこを含めることはできません。  
  
 値が引用符で囲まれている場合でも、リテラルとして解釈されます、接続文字列キーワードの等号 (=) 後のスペース文字。  
  
 次の表に、DBPROP_INIT_PROVIDERSTRING と共に使用できるキーワードを示します。  
  
|Keyword|初期化プロパティ|Description|  
|-------------|-----------------------------|-----------------|  
|**addr**|SSPROP_INIT_NETWORKADDRESS|"Address" のシノニム。|  
|**Address**|SSPROP_INIT_NETWORKADDRESS|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスを実行しているサーバーのネットワーク アドレス。 **アドレス**は通常、サーバーのネットワーク名が、パイプ、IP アドレス、または TCP/IP ポートとソケット アドレスなど他の名前を指定できます。<br /><br /> IP アドレスを指定する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで TCP/IP または名前付きパイプ プロトコルが有効になっていることを確認します。<br /><br /> 値**アドレス**に渡された値よりも優先**サーバー** SQL Server の OLE DB Driver を使用する場合、接続文字列にします。 またを注意してください`Address=;`で指定したサーバーに接続する、**サーバー**キーワード、一方`Address= ;, Address=.;`、 `Address=localhost;`、および`Address=(local);`すべてが原因で、ローカル サーバーに接続します。<br /><br /> 完全な構文、**アドレス**キーワードのとおりです。<br /><br /> [*プロトコル ***:**]* アドレス *[* *、* * * ポート&#124;\pipe\pipename*]<br /><br /> *protocol* には、 **tcp** (TCP/IP)、 **lpc** (共有メモリ)、または **np** (名前付きパイプ) を指定できます。 プロトコルの詳細については、次を参照してください。 [Configure Client Protocols](../../../database-engine/configure-windows/configure-client-protocols.md)です。<br /><br /> どちらの場合*プロトコル*も**ネットワーク**キーワードを指定すると、OLE DB Driver for SQL Server がで指定されたプロトコルの順序を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager です。<br /><br /> *ポート*に接続する、指定したサーバー上のポートです。 既定では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はポート 1433 を使用します。|   
|**APP**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。<br /><br /> 既定値は**ReadWrite**です。 SQL Server のサポートの OLE DB ドライバーの詳細については[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL サーバーが高可用性、災害復旧のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 使用する**AttachDBFileName**、プロバイダー文字列の Database キーワードでデータベース名を指定することも必要があります。 場合は、データベースは、以前にアタッチされて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に再アタッチしません (、アタッチされたデータベースの既定値として接続に使用)。|  
|**Auto Translate します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "yes" と "no" です。|  
|**データベース**|DBPROP_INIT_CATALOG|データベース名です。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|データ型を使用する処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および SQL Server 2000 データ型を示す "80" です。|  
|**Encrypt**|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server、既定では、プロバイダーが生成した SPN を使用するとします。|  
|**言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語。|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のサーバーの場合)。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|常に指定**MultiSubnetFailover = [はい]** の可用性グループ リスナーに接続するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]可用性グループ、または[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。 **MultiSubnetFailover = Yes** OLE DB Driver for SQL Server を迅速に検出し、(現在) アクティブなサーバーへの接続を提供するように構成します。 可能な値は **Yes** と **No**です。 既定値は**いいえ**です。 以下に例を示します。<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> SQL Server のサポートの OLE DB ドライバーの詳細については[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL サーバーが高可用性、災害復旧のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|  
|**net**|SSPROP_INIT_NETWORKLIBRARY|"Network" のシノニム。|  
|**ネットワーク**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**ネットワーク ライブラリ**|SSPROP_INIT_NETWORKLIBRARY|"Network" のシノニム。|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "yes" と "no" を値として受け取ります。 "no" の場合、データ ソース オブジェクトには機密の認証情報を保存できません。|  
|**PWD**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**[サーバー]**|DBPROP_INIT_DATASOURCE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前。 ネットワーク上のサーバーの名前、IP アドレス、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーの別名を指定する必要があります。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> **アドレス**キーワードよりも優先、**サーバー**キーワード。<br /><br /> ローカル サーバーの既定のインスタンスに接続するには、次のいずれかを指定します。<br /><br /> **サーバー = です。**<br /><br /> **サーバー =。 です。**<br /><br /> **Server=(local) です。**<br /><br /> **Server=(local) です。**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** *instancename* **;**<br /><br /> LocalDB のサポートの詳細については、次を参照してください。 [OLE DB Driver for SQL Server で LocalDB のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)です。<br /><br /> 名前付きインスタンスを指定する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、追加 **\\ ***InstanceName*です。<br /><br />サーバーが指定されていない場合、ローカル コンピューター上の既定のインスタンス、接続を確立します。<br /><br />IP アドレスを指定する場合で TCP/IP または名前付きパイプ プロトコルが有効になっていることを確認してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager です。<br /><br />完全な構文、**サーバー**キーワードのとおりです:<br /> <br /> **サーバー =**[* プロトコル***:**]*サーバー*[**、* * * ポート*]<br /><br /> *protocol* には、 **tcp** (TCP/IP)、 **lpc** (共有メモリ)、または **np** (名前付きパイプ) を指定できます。<br /><br /> 名前付きパイプを指定する例を次に示します。<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> この行では、名前付きパイプのプロトコル、ローカル コンピューター上の名前付きパイプ (`\\.\pipe`)、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前 (`MSSQL$MYINST01`)、および名前付きパイプの既定の名前 (`sql/query`) を指定しています。<br /><br /> どちらの場合、*プロトコル*も**ネットワーク**キーワードを指定すると、OLE DB Driver for SQL Server がで指定されたプロトコルの順序を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager です。<br /><br /> *ポート*に接続する、指定したサーバー上のポートです。 既定では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はポート 1433 を使用します。<br /><br /> 渡される値の先頭のスペースは無視されます**サーバー** SQL Server の OLE DB Driver を使用する場合、接続文字列にします。|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server、既定では、プロバイダーが生成した SPN を使用するとします。|  
|**Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|ときに、OLE DB Driver for SQL Server ログインの検証に Windows 認証モードを使用するように指示"yes"します。 それ以外の場合、OLE DB Driver for SQL Server を使用するよう指示、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ユーザー名とログインの検証、および、UID キーワードと PWD キーワードのパスワードを指定する必要があります。|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "yes" と "no" を値として受け取ります。 既定値は "no" です。これはサーバー証明書が検証されることを示します。|  
|**UID**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|このキーワードは推奨されず、および SQL Server の OLE DB Driver でその設定は無視されます。|  
|**WSID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
 使用して OLE DB アプリケーションで使用される接続文字列**idatainitialize::getdatasource**次の構文します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 プロパティの使用方法は、プロパティのスコープで許可される構文に従っている必要があります。  たとえば、 **WSID**中かっこを使用して (**{}**) 引用符の文字と**アプリケーション名**では一重 (**'**) または二重 (**"**) 引用符文字。 引用符で囲むことができるのは、文字列のプロパティのみです。 整数または列挙のプロパティを引用符で囲むと、"接続文字列は OLE DB 仕様に準拠していません" というエラーが発生します。  
  
 属性値は必要に応じて一重引用符または二重引用符で囲むことができます。常にこれらの引用符を使用すると、 値に英数字以外の文字が含まれる場合の問題を回避できます。 二重引用符の場合は、値の中に含めることもできます。  
  
 値が引用符で囲まれている場合でも、リテラルとして解釈されます、接続文字列キーワードの等号 (=) 後のスペース文字。  
  
 接続文字列に次の表のプロパティが複数含まれている場合は、最後のプロパティの値が使用されます。  
  
 次の表に、キーワードと共に使用できるを**idatainitialize::getdatasource**:  
  
|Keyword|初期化プロパティ|Description|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**アプリケーションの目的**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。<br /><br /> 既定値は**ReadWrite**です。 SQL Server のサポートの OLE DB ドライバーの詳細については[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL サーバーが高可用性、災害復旧のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|  
|**Auto Translate します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "true" と "false" です。|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**現在の言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前。|  
|**[データ ソース]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**サーバー**キーワードは、このトピックの「します。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|データ型を使用する処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] データ型を示す "80" です。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**フェールオーバー パートナー SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server、既定では、プロバイダーが生成した SPN を使用するとします。|  
|**初期カタログ**|DBPROP_INIT_CATALOG|データベース名です。|  
|**初期ファイル名**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 使用する**AttachDBFileName**、プロバイダー文字列の DATABASE キーワードでデータベース名を指定することも必要があります。 場合は、データベースは、以前にアタッチされて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に再アタッチしません (、アタッチされたデータベースの既定値として接続に使用)。|  
|**統合セキュリティ**|DBPROP_AUTH_INTEGRATED|Windows 認証の値 "SSPI" を受け取ります。|  
|**MARS 接続**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします。 認識できる値は "true" と "false" です。 既定値は "false" です。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|常に指定**MultiSubnetFailover = True**の可用性グループ リスナーに接続するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]可用性グループ、または[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。 **MultiSubnetFailover = True** OLE DB Driver for SQL Server を迅速に検出し、(現在) アクティブなサーバーへの接続を提供するように構成します。 指定できる値は、 **[True]** および **[False]** です。 既定値は **False**です。 以下に例を示します。<br /><br /> `MultiSubnetFailover=True`<br /><br /> SQL Server のサポートの OLE DB ドライバーの詳細については[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL サーバーが高可用性、災害復旧のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|  
|**ネットワーク アドレス**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**アドレス**キーワードは、このトピックの「します。|  
|**ネットワーク ライブラリ**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**Password**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "true" と "false" を値として受け取ります。 機微な認証情報を保持するデータ ソース オブジェクトが許可されていません"false"の場合|  
|**プロバイダー**||OLE DB driver for SQL Server、"MSOLEDBSQL"があります。|  
|**サーバーの SPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server、既定では、プロバイダーが生成した SPN を使用するとします。|  
|**[Trust Server Certificate]**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "true" と "false" を値として受け取ります。 既定値は "false" です。これはサーバー証明書が検証されることを示します。|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 指定できる値は "true" と "false" です。 既定値は"false"です。|  
|**[ユーザー ID]**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**ワークステーション ID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
 **注**接続文字列で"Old Password"プロパティを設定 SSPROP_AUTH_OLD_PASSWORD、これは、現在 (または期限切れの) はないパスワードをプロバイダー文字列のプロパティ経由で入手できます。  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>ADO (ActiveX Data Objects) の接続文字列のキーワード  
 ADO アプリケーション セット、 **ConnectionString**プロパティの**ADODBConnection**オブジェクトまたはパラメーターとして接続文字列を指定、**開く**メソッドの**ADODBConnection**オブジェクト。  
  
 ADO アプリケーションでは、OLE DB で使用されるキーワードを使用できますも**idbinitialize::initialize**メソッドは、既定値がないプロパティについては、します。 アプリケーションが ADO キーワードを使用する場合、 **idbinitialize::initialize**初期化文字列、ADO キーワードの設定でキーワードが使用されます。 アプリケーションでは ADO 接続文字列のキーワードのみを使用することを強くお勧めします。  
  
 ADO で使用される接続文字列の構文を次に示します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて二重引用符で囲むことができます。常に二重引用符を使用すると、 値に英数字以外の文字が含まれる場合の問題を回避できます。 属性値に二重引用符を含めることはできません。  
  
 次の表に、ADO 接続文字列と共に使用できるキーワードを示します。  
  
|Keyword|初期化プロパティ|Description|  
|-------------|-----------------------------|-----------------|  
|**アプリケーションの目的**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。<br /><br /> 既定値は**ReadWrite**です。 SQL Server のサポートの OLE DB ドライバーの詳細については[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL サーバーが高可用性、災害復旧のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|  
|**Application Name**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**Auto Translate します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "true" と "false" です。|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**現在の言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前。|  
|**[データ ソース]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**サーバー**キーワードは、このトピックの「します。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|使用するデータ型処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および SQL Server 2000 データ型を示す "80" です。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**フェールオーバー パートナー SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server、既定では、プロバイダーが生成した SPN を使用するとします。|  
|**初期カタログ**|DBPROP_INIT_CATALOG|データベース名です。|  
|**初期ファイル名**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 使用する**AttachDBFileName**、プロバイダー文字列の DATABASE キーワードでデータベース名を指定することも必要があります。 場合は、データベースは、以前にアタッチされて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に再アタッチしません (、アタッチされたデータベースの既定値として接続に使用)。|  
|**統合セキュリティ**|DBPROP_AUTH_INTEGRATED|Windows 認証の値 "SSPI" を受け取ります。|  
|**MARS 接続**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のサーバーの場合)。 認識できる値は "true" と "false" です。既定値は "false" です。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|常に指定**MultiSubnetFailover = True**の可用性グループ リスナーに接続するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]可用性グループ、または[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。 **MultiSubnetFailover = True** OLE DB Driver for SQL Server を迅速に検出し、(現在) アクティブなサーバーへの接続を提供するように構成します。 指定できる値は、 **[True]** および **[False]** です。 既定値は **False**です。 以下に例を示します。<br /><br /> `MultiSubnetFailover=True`<br /><br /> SQL Server のサポートの OLE DB ドライバーの詳細については[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[OLE DB Driver for SQL サーバーが高可用性、災害復旧のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|  
|**ネットワーク アドレス**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**アドレス**キーワードは、このトピックの「します。|  
|**ネットワーク ライブラリ**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**Password**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "true" と "false" を値として受け取ります。 "false" の場合、データ ソース オブジェクトには機密の認証情報を保存できません。|  
|**プロバイダー**||OLE DB driver for SQL Server、"MSOLEDBSQL"があります。|  
|**サーバーの SPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列は、OLE DB Driver for SQL Server、既定では、プロバイダーが生成した SPN を使用するとします。|  
|**[Trust Server Certificate]**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "true" と "false" を値として受け取ります。 既定値は "false" です。これはサーバー証明書が検証されることを示します。|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 指定できる値は "true" と "false" です。 既定値は"false"です。|  
|**[ユーザー ID]**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**ワークステーション ID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
 **注**接続文字列で"Old Password"プロパティを設定 SSPROP_AUTH_OLD_PASSWORD、これは、現在 (または期限切れの) はないパスワードをプロバイダー文字列のプロパティ経由で入手できます。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
