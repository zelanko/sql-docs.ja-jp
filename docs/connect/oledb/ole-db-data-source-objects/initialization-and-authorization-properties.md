---
title: 初期化プロパティと承認プロパティ |Microsoft ドキュメント
description: プロパティの初期化と承認プロパティ
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- authorization [OLE DB]
- properties [OLE DB]
- OLE DB Driver for SQL Server, initialization properties
- OLE DB Driver for SQL Server, authorization properties
- initialization properties [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6be9ab05f9f7a5c669e62f92c238be3d06dbf44d
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="initialization-and-authorization-properties"></a>初期化プロパティと承認プロパティ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server では、OLE DB 初期化と承認プロパティが次のように解釈されます。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_AUTH_CACHE_AUTHINFO|SQL Server の OLE DB Driver は、認証情報をキャッシュしません。<br /><br /> SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_AUTH_ENCRYPT_PASSWORD|SQL Server の OLE DB Driver は、標準を使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]パスワードを隠しますセキュリティ メカニズム。<br /><br /> SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_AUTH_INTEGRATED|If DBPROP_AUTH_INTEGRATED is set to a NULL pointer, a null string, or 'SSPI' VT_BSTR value, the OLE DB Driver for SQL Server uses Windows Authentication Mode to authorize user access to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database specified by the DBPROP_INIT_DATASOURCE and DBPROP_INIT_CATALOG properties.<br /><br /> VT_EMPTY (既定値) に設定すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セキュリティが使用されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインとパスワードは、DBPROP_AUTH_USERID プロパティと DBPROP_AUTH_PASSWORD プロパティで指定されます。|  
|DBPROP_AUTH_MASK_PASSWORD|SQL Server の OLE DB Driver は、標準を使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]パスワードを隠しますセキュリティ メカニズム。<br /><br /> SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに割り当てられたパスワードです。 このプロパティは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへのアクセスの承認に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証が選択された場合に使用されます。|  
|DBPROP_AUTH_PERSIST_ENCRYPTED|SQL Server の OLE DB ドライバーでは、保存されるときに、認証情報は暗号化されません。<br /><br /> SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|SQL Server の OLE DB Driver は、するように要求されている場合に、パスワードのイメージを含めて、認証の値を維持します。 暗号化は行われません。|  
|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインです。 このプロパティは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへのアクセスの承認に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証が選択された場合に使用されます。|  
|DBPROP_INIT_ASYNCH|SQL Server の OLE DB Driver は、非同期の初期化をサポートします。<br /><br /> Dbprop_init_asynch プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定**idbinitialize::initialize**に非ブロッキング呼び出しになります。 詳細については、次を参照してください。[非同期操作の実行](../../oledb/features/performing-asynchronous-operations.md)です。|  
|DBPROP_INIT_CATALOG|接続先の既存の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース名です。|  
|DBPROP_INIT_DATASOURCE|インスタンスを実行しているサーバーのネットワーク名[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 複数のインスタンスがある場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の特定のインスタンスに接続するために、コンピューターで実行されている[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]として DBPROP_INIT_DATASOURCE が指定された値 *\\\ServerName\InstanceName*です。 エスケープ シーケンス\\\ 円記号自体のために使用します。|  
|DBPROP_INIT_GENERALTIMEOUT|データ ソースの初期化とコマンドの実行以外の要求がタイムアウトするまでの秒数を示します。値 0 は、タイムアウトしないことを表します。プロバイダーがネットワーク接続経由で動作している場合、または分散シナリオやトランザクション シナリオで実行されている場合、このプロパティをサポートすることで、実行時間の長い要求が発生した際に、参加しているコンポーネントに対してタイムアウトするよう指示できます。 データ ソースの初期化とコマンド実行のタイムアウトについては、それぞれ DBPROP_INIT_TIMEOUT と DBPROP_COMMANDTIMEOUT で指定されます。<br /><br /> DBPROP_INIT_GENERALTIMEOUT は読み取り専用に設定しようとすると 1 つと、 *dwstatus* DBPROPSTATUS_NOTSETTABLE のエラーが返されます。|  
|DBPROP_INIT_HWND|呼び出し元アプリケーションのウィンドウ ハンドルです。 初期化プロパティに入力要求が許可されている場合は、初期化ダイアログ ボックスを表示するために、有効なウィンドウ ハンドルが必要です。|  
|DBPROP_INIT_IMPERSONATION_LEVEL|SQL Server の OLE DB Driver は、権限借用レベルの調整をサポートしていません。<br /><br /> SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_INIT_LCID|OLE DB Driver for SQL Server では、ロケール ID を検証し、ロケール ID がサポートされていないか、クライアントにインストールされていない場合、エラーを返します。|  
|DBPROP_INIT_LOCATION|SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_INIT_MODE|SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_INIT_PROMPT|SQL Server の OLE DB Driver は、データ ソースの初期化のすべての入力要求モードをサポートします。 SQL Server の OLE DB Driver は、プロパティの既定の設定として DBPROMPT_NOPROMPT を使用します。|  
|DBPROP_INIT_PROTECTION_LEVEL|SQL Server の OLE DB Driver がのインスタンスへの接続上の保護レベルをサポートしていません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。<br /><br /> SQL Server の OLE DB Driver は、プロパティ値を設定しようとすると、DB_S_ERRORSOCCURRED を返します。 *DwStatus* DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を示します。|  
|DBPROP_INIT_PROVIDERSTRING|このトピックの「SQL Server 文字列の OLE DB ドライバーを参照してください。|  
|DBPROP_INIT_TIMEOUT|SQL Server の OLE DB ドライバー エラーが返されます初期化時に接続のインスタンスに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]指定された秒数内で確立することはできません。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDBINIT では、SQL Server の OLE DB Driver は、これらの追加の初期化プロパティを定義します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_AUTH_OLD_PASSWORD|型 : VT_BSTR<br /><br /> R/W: 書き込み<br /><br /> 既定値 : VT_EMPTY<br /><br /> 説明: 現在のパスワードまたは有効期限が切れたパスワードです。 詳細については、次を参照してください。[プログラムでパスワードを変更する](../../oledb/features/changing-passwords-programmatically.md)です。|  
|SSPROP_INIT_APPNAME|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: クライアント アプリケーション名です。|  
|SSPROP_INIT_AUTOTRANSLATE|型 : VT_BOOL<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_TRUE<br /><br /> 説明: OEM/ANSI 文字変換です。<br /><br /> VARIANT_TRUE: SQL Server の OLE DB Driver は、クライアント上のコード ページと、サーバーの間で拡張文字の照合における問題を最小限に抑えるには Unicode を通じて変換することで、クライアントとサーバーの間で送信される ANSI 文字列を変換します。<br /><br /> インスタンスに送信されるクライアントの DBTYPE_STR データ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**、 **varchar**、または**テキスト**変数、パラメーター、または列が文字からクライアントの ANSI コード ページ (ACP) を使用して Unicode に変換し、サーバーの acp に基づいて文字を Unicode から変換されます。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**char**、 **varchar**、または**テキスト**クライアントの DBTYPE_STR 変数に送信されるデータが文字からサーバーの acp に基づいて Unicode に変換し、クライアントの acp に基づいて文字を Unicode から変換されます。<br /><br /> これらの変換は、SQL Server の OLE DB ドライバーによってクライアントで実行されます。 そのため、サーバーで使用しているものと同じ ACP がクライアントでも使用可能になっている必要があります。<br /><br /> 次の設定は、送受信時の変換に影響しません。<br /><br /> 送信される Unicode の DBTYPE_WSTR クライアント データ**char**、 **varchar**、または**テキスト**サーバーにします。<br /><br /> **char**、 **varchar**、または**テキスト**サーバー データのクライアントの Unicode の DBTYPE_WSTR 変数に送信します。<br /><br /> Unicode に送信される ANSI DBTYPE_STR クライアント データ**nchar**、 **nvarchar**、または**ntext**サーバーにします。<br /><br /> Unicode **char**、 **varchar**、または**テキスト**サーバー データのクライアントの ANSI DBTYPE_STR 変数に送信します。<br /><br /> VARIANT_FALSE: SQL Server の OLE DB Driver は、文字変換を実行しません。<br /><br /> OLE DB Driver for SQL Server に送信されるクライアント ANSI 文字の DBTYPE_STR データに変換されない**char**、 **varchar**、または**テキスト**変数、パラメーター、または列をサーバー。 変換は実行されません**char**、 **varchar**、または**テキスト**クライアントの DBTYPE_STR 変数に、サーバーから送信されるデータ。<br /><br /> クライアントと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスが使用する ACP が異なる場合、拡張文字の解釈が正しく行われない場合があります。|  
|SSPROP_INIT_CURRENTLANGUAGE|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の言語名です。 システム メッセージの選択や書式設定に使われる言語を示します。 指定された言語が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスを実行するコンピューターにインストールされていないと、データ ソースの初期化が失敗します。|  
|SSPROP_INIT_DATATYPECOMPATIBILITY|型: VT_UI2<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値: 0<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と ActiveX Data Object (ADO) アプリケーション間のデータ型の互換性を確保します。 既定値の 0 が使用されている場合、データ型の処理では、プロバイダーが既定で使用するデータ型が使われます。 値 80 が使用されている場合、データ型の処理では、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] のデータ型しか使われません。 詳細については、次を参照してください。 [ADO を使用して OLE DB Driver for SQL Server と](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md)です。|  
|SSPROP_INIT_ENCRYPT|型 : VT_BOOL<br /><br /> R/W: 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明: ネットワーク経由で転送されるデータを暗号化する場合は、SSPROP_INIT_ENCRYPT プロパティを VARIANT_TRUE に設定します。<br /><br /> プロトコルの暗号化が有効な場合は、SSPROP_INIT_ENCRYPT の設定に関係なく、常に暗号化が行われます。 プロトコルの暗号化が無効な場合でも、SSPROP_INIT_ENCRYPT が VARIANT_TRUE に設定されている場合は、暗号化が行われます。<br /><br /> プロトコルの暗号化が無効で、SSPROP_INIT_ENCRYPT が VARIANT_FALSE に設定されている場合は、暗号化は行われません。|  
|SSPROP_INIT_FAILOVERPARTNER|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: データベース ミラーリングのフェールオーバー パートナーの名前を示します。 これは、初期化プロパティで、初期化前にしか設定できません。 初期化後は、フェールオーバー パートナーが構成されている場合は、プライマリ サーバーから返されたフェールオーバー パートナー名を返します。<br /><br /> これにより、アプリケーションで、最後に判別したバックアップ サーバーのキャッシュが、このようなアプリケーションはこと情報が、接続が最初の更新だけ確立 (かリセット、プールされている場合) に注意してください長期的な接続の期限切れになることができます。<br /><br /> 接続後は、アプリケーションでこの属性をクエリすることにより、フェールオーバー パートナーの ID を判別できます。 プライマリ サーバーのフェールオーバー パートナーが存在しないと、この属性は空文字列を返します。 詳細については、次を参照してください。 [Using Database Mirroring](../../oledb/features/using-database-mirroring.md)です。|  
|SSPROP_INIT_FILENAME|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: アタッチできるデータベースのプライマリ ファイル名を示します。 このデータベースがアタッチされ、接続の既定のデータベースとして使用されます。 SSPROP_INIT_FILENAME を使用するには、初期化プロパティ DBPROP_INIT_CATALOG の値にデータベース名を指定する必要があります。 指定したデータベース名が存在しない場合は、SSPROP_INIT_FILENAME に指定されているプライマリ ファイル名を確認し、そのデータベースと DBPROP_INIT_CATALOG に指定されている名前とをアタッチします。 データベースが以前にアタッチされていた場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はこれを再アタッチしません。|  
|SSPROP_INIT_MARSCONNECTION|型 : VT_BOOL<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明: 複数のアクティブな結果セット (MARS) が接続で有効かどうかを示します。 このオプションは、データベースへの接続が確立される前に、TRUE に設定する必要があります。 詳細については、次を参照してください。[複数のアクティブな結果セットの使用 &#40;です。MARS &#41;](../../oledb/features/using-multiple-active-result-sets-mars.md).|  
|SSPROP_INIT_NETWORKADDRESS|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: DBPROP_INIT_DATASOURCE プロパティで指定されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスを実行するサーバーのネットワーク アドレスです。|  
|SSPROP_INIT_NETWORKLIBRARY|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスとの通信に使われるネットワーク ライブラリ (DLL) の名前です。 この名前には、パスやファイル拡張子 (.dll) は含めません。<br /><br /> 既定値は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント構成ユーティリティを使用してカスタマイズできます。<br /><br /> 注: のみの TCP と名前付きパイプは、このプロパティでサポートされます。 このプロパティにプレフィックスを使用した場合、プレフィックスが二重になりエラーが発生します。これは、内部でこのプロパティを使用してプレフィックスが生成されるためです。|  
|SSPROP_INIT_PACKETSIZE|型 : VT_I4<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: ネットワーク パケットのバイト単位のサイズです。 このパケット サイズ プロパティの値は 512 ～ 32,767 にする必要があります。 SQL Server のネットワーク パケット サイズの既定の OLE DB Driver は、4,096 です。|  
|SSPROP_INIT_TAGCOLUMNCOLLATION|型: BOOL <br /><br /> R/W: 書き込み<br /><br /> 既定値: FALSE <br /><br /> 説明: サーバー側カーソルが使用されているとき、データベースの更新中に使用されます。 このプロパティは、クライアントのコード ページではなく、サーバーから取得した照合順序情報を使用してデータにタグを付けます。 現在、このプロパティは、分散クエリ プロセスでしか使われていません。これは、分散クエリ プロセスでは変換先データの照合順序が認識されていて、データが適切に変換されるためです。|  
|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|型 : VT_BOOL<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明: サーバー証明書の検証の有効化または無効化に使用されます。 このプロパティは読み取り/書き込みですが、接続の確立後にこの値の設定が試みられると、エラーが発生します。<br /><br /> このプロパティは、クライアントが証明書の検証を要求するよう構成されている場合は、無視されます。 ただし、アプリケーションは、このプロパティを SSPROP_INIT_ENCRYPT と共に使用して、クライアントが暗号化を要求するよう構成されておらず、証明書がクライアント側に準備されていない場合でも、アプリケーションとサーバー間の接続が確実に暗号化されるようにすることができます。<br /><br /> クライアント アプリケーションでは、接続を開いた後にこの属性をクエリして、実際に使用されている暗号化と検証の設定を判断できます。<br /><br /> 注: 暗号化を使用して証明書がない検証パケット スニッフィングに対して、部分的な保護には中間の攻撃から保護することはできません。 この場合、サーバー証明書を検証せずに、サーバーに送られるログインとデータの暗号化が行われます。<br /><br /> 詳細については、次を参照してください。[を使用して検証を伴わない暗号化](../../oledb/features/using-encryption-without-validation.md)です。|  
|SSPROP_INIT_USEPROCFORPREP|型 : VT_I4<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値: SSPROPVAL_USEPROCFORPREP_ON <br /><br /> 説明: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャを使用するかどうか。 使用を定義[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]一時ストアド プロシージャをサポートするために、 **ICommandPrepare**インターフェイスです。 このプロパティは SQL Server 6.5 に接続するときに限り意味がありました。 これ以降のバージョンでは、このプロパティは無視されます。<br /><br /> SSPROPVAL_USEPROCFORPREP_OFF: コマンドを準備するときには、一時ストアド プロシージャが作成されません。<br /><br /> SSPROPVAL_USEPROCFORPREP_ON: コマンドを準備するときに、一時ストアド プロシージャが作成されます。 セッションが解放されると、作成された一時ストアド プロシージャは削除されます。<br /><br /> SSPROPVAL_USEPROCFORPREP_ON_DROP: コマンドを準備するときに、一時ストアド プロシージャが作成されます。 コマンドは、準備ができていませんのときに、プロシージャが削除される**ICommandPrepare::Unprepare**、使用してコマンド オブジェクトの新しいコマンドを指定すると**icommandtext::setcommandtext**のコマンドは、すべてのアプリケーション参照がリリースされたときまたはします。|  
|SSPROP_INIT_WSID|型 : VT_BSTR<br /><br /> R/W 読み取り/書き込み<br /><br /> 説明: ワークステーションを識別する文字列です。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDATASOURCEINFO で、OLE DB Driver for SQL Server が、追加のプロパティを定義します。参照してください[データ ソース情報プロパティ](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)詳細についてはします。  
  
## <a name="the-ole-db-driver-for-sql-server-string"></a>SQL Server 文字列用の OLE DB ドライバー  
 SQL Server の OLE DB Driver は、プロバイダー文字列のプロパティの値として、ODBC のような構文を認識します。 プロバイダーの文字列プロパティは、OLE DB データ ソースへの接続が確立される時点で、OLE DB 初期化プロパティ DBPROP_INIT_PROVIDERSTRING の値として提供されます。 このプロパティは、OLE DB データ ソースへの接続の実装に必要な OLE DB プロバイダー固有の接続データを示します。 この文字列内では、要素がセミコロンを使用して区切られます。 文字列の最後の要素には、セミコロンを付けて、終端を示す必要があります。 各要素は、キーワード、等号文字、初期化時に渡される値で構成されます。 以下に例を示します。  
  
```  
Server=MyServer;UID=MyUserName;  
```  
  
 OLE DB Driver for SQL Server、コンシューマーはプロバイダー文字列のプロパティを使用する必要はありません。 コンシューマーは、OLE DB、または OLE DB Driver プロパティを使って SQL Server に固有の初期化によって、プロバイダー文字列に反映される任意の初期化プロパティを設定できます。  
  
 SQL Server の OLE DB ドライバーで使用できるキーワードの一覧は、次を参照してください。 [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)です。  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
