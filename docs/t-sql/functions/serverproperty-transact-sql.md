---
title: "SERVERPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVERPROPERTY_TSQL
- SERVERPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SERVERPROPERTY function
- server instance property information [SQL Server]
- IsHadrEnabled server property
- instances of SQL Server, property information
- server properties [SQL Server]
ms.assetid: 11e166fa-3dd2-42d8-ac4b-04f18c612c4a
caps.latest.revision: 128
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7060a8aaf668a69184503fa0995dd4f37085d5f1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="serverproperty-transact-sql"></a>SERVERPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  サーバー インスタンスについてのプロパティ情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SERVERPROPERTY ( 'propertyname' )  
```  
  
## <a name="arguments"></a>引数  
 *プロパティ名*  
 サーバーについて、返されるプロパティ情報を含む式を指定します。 *propertyname*値は次のいずれかになります。  
  
|プロパティ|返される値|  
|--------------|---------------------|  
|BuildClrVersion|バージョン、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]のインスタンスの構築時に使用された共通言語ランタイム (CLR)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **nvarchar (128)**|  
|[照合順序]|サーバーの既定の照合順序の名前。<br /><br /> NULL = 入力が無効、または、エラーが発生します。<br /><br /> 基本データ型: **nvarchar (128)**|  
|CollationID|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序の ID。<br /><br /> 基本データ型: **int**|  
|ComparisonStyle|照合順序の Windows 比較形式。<br /><br /> 基本データ型: **int**|  
|ComputerNamePhysicalNetBIOS|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが現在実行されているローカル コンピューターの NetBIOS 名。<br /><br /> フェールオーバー クラスターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クラスター化インスタンスでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがフェールオーバー クラスターの他のノードにフェールオーバーすると、この値が変わります。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スタンドアロン インスタンスではこの値は変わらず、MachineName プロパティと同じ値が返されます。<br /><br /> **注:**場合のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がフェールオーバー クラスターしたい場合、フェールオーバー クラスター インスタンスの名前を取得、MachineName プロパティを使用します。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **nvarchar (128)**|  
|のエディション|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのインストールされている製品のエディション。 このプロパティの値を使用して、機能と、制限をなどを判断する[Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)です。 このバージョン (64 ビット) には、64 ビット バージョンの[!INCLUDE[ssDE](../../includes/ssde-md.md)]が追加されています。<br /><br /> 戻り値:<br /><br /> 'Enterprise Edition'<br /><br /> ‘Enterprise Edition: Core-based Licensing’<br /><br /> 'Enterprise Evaluation Edition'<br /><br /> ‘Business Intelligence Edition’<br /><br /> 'Developer Edition'<br /><br /> 'Express Edition'<br /><br /> 'Express Edition with Advanced Services'<br /><br /> 'Standard Edition'<br /><br /> 'Web Edition'<br /><br /> ' SQL Azure' 示す[!INCLUDE[ssSDS](../../includes/sssds-md.md)]または[!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> 基本データ型: **nvarchar (128)**|  
|EditionID|EditionID は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスについて、インストールされている製品のエディションを表します。 このプロパティの値を使用して、機能と制限をなどを決定する[Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)です。<br /><br /> 1804890536 = Enterprise<br /><br /> 1872460670 = Enterprise Edition: Core-based Licensing<br /><br /> 610778273= Enterprise Evaluation<br /><br /> 284895786 = Business Intelligence<br /><br /> -2117995310 = Developer<br /><br /> -1592396055 = Express<br /><br /> -133711905 express with Advanced Services を =<br /><br /> -1534726760 = 標準<br /><br /> 1293598313 = Web<br /><br /> 1674378470 = SQL データベースまたは SQL Data Warehouse<br /><br /> 基本データ型: **bigint**|  
|EngineEdition|サーバーにインストールされている [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエディション。<br /><br /> 1 = personal または Desktop Engine (で利用できない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンです)。<br /><br /> 2 = Standard (Standard、Web、および Business Intelligence の場合に返されます)<br /><br /> 3 = Enterprise (Evaluation、Developer、および両方の Enterprise エディションの場合にこの値が返されます)<br /><br /> 4 = Express (Express、Express with Tools、および Express with Advanced Services の場合に返されます)<br /><br /> 5 = [!INCLUDE[ssSDS](../../includes/sssds-md.md)]<br /><br /> 6 - [!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> 基本データ型: **int**|  
|HadrManagerStatus|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] マネージャーが開始されたかどうかを示します。<br /><br /> 0 = 未開始状態、通信保留中<br /><br /> 1 = 開始されて実行中<br /><br /> 2 = 未開始状態、失敗<br /><br /> NULL = 無効な入力、エラー、または該当なし|  
|InstanceDefaultDataPath|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> 既定のパス、インスタンス データ ファイルの名前です。|  
|InstanceDefaultLogPath|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> インスタンスのログ ファイルを既定のパスの名前です。|  
|InstanceName|ユーザーの接続先のインスタンス名。<br /><br /> インスタンス名が既定インスタンスの場合や、無効な入力またはエラーの場合は、NULL が返されます。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **nvarchar (128)**|  
|IsAdvancedAnalyticsInstalled|セットアップ時に Advanced Analytics 機能がインストールされている場合は 1 を返します。Advanced Analytics がインストールされていない場合は 0 を返します。|  
|IsClustered|サーバー インスタンスがフェールオーバー クラスターで構成されます。<br /><br /> 1 = クラスター化<br /><br /> 0 = 非クラスター化<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**|  
|IsFullTextInstalled|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスに、フルテキスト インデックス作成およびセマンティック インデックス作成のコンポーネントがインストールされています。<br /><br /> 1 = フルテキスト インデックス作成およびセマンティック インデックス作成のコンポーネントがインストールされています。<br /><br /> 0 = フルテキスト インデックス作成およびセマンティック インデックス作成のコンポーネントがインストールされていません。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**|  
|IsHadrEnabled|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]は、このサーバー インスタンス上で有効です。<br /><br /> 0 = [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]機能は無効です。<br /><br /> 1 = [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]機能は有効です。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで可用性レプリカを作成して実行するには、サーバー インスタンス上で [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]が有効になっている必要があります。 詳細については、次を参照してください。[の有効化および無効にする AlwaysOn 可用性グループ (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)です。<br /><br /> **注:** IsHadrEnabled プロパティがだけに関連[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]です。 データベース ミラーリングやログ配布などの、その他の高可用性機能およびディザスター リカバリー機能は、このサーバー プロパティの影響を受けません。|  
|IsIntegratedSecurityOnly|サーバーは統合セキュリティ モードです。<br /><br /> 1 = 統合セキュリティ (Windows 認証)<br /><br /> 0 = 非統合セキュリティ (Windows 認証と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証の両方)。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**|  
|IsLocalDB|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> サーバーは [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] LocalDB のインスタンスです。<br /><br /> NULL = 無効な入力、エラー、または該当なし|  
|IsPolybaseInstalled|**適用対象**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> サーバー インスタンスがインストールされている PolyBase 機能を持つかどうかを返します。<br /><br /> 0 = PolyBase がインストールされていません。<br /><br /> 1 = PolyBase がインストールされています。<br /><br /> 基本データ型: **int**|  
|IsSingleUser|サーバーはシングル ユーザー モードです。<br /><br /> 1 = シングル ユーザー<br /><br /> 0 = 非シングル ユーザー<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**|  
|IsXTPSupported|**適用されます**: SQL Server ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。<br /><br /> サーバーは、インメモリ OLTP をサポートします。<br /><br /> 1 = サーバーはインメモリ OLTP をサポートします。<br /><br /> 0 = サーバーはインメモリ OLTP をサポートしません。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**|  
|LCID (LCID)|照合順序の Windows ロケール識別子 (LCID)。<br /><br /> 基本データ型: **int**|  
|LicenseType|未使用。 ライセンス情報は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 製品によって保存または維持されていません。 常に DISABLED が返されます。<br /><br /> 基本データ型: **nvarchar (128)**|  
|MachineName|サーバー インスタンスが稼働している Windows コンピューターの名前。<br /><br /> クラスター化インスタンスの場合、つまり、Microsoft Cluster Service 上の仮想サーバーで稼働している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの場合は、仮想サーバーの名前が返されます。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **nvarchar (128)**|  
|NumLicenses|未使用。 ライセンス情報は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 製品によって保存または維持されていません。 常に NULL が返されます。<br /><br /> 基本データ型: **int**|  
|ProcessID|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスのプロセス ID。 このインスタンスに属する Sqlservr.exe を識別するときに、ProcessID は効果的です。<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: **int**|  
|ProductBuild|**適用されます**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 2015 年 10 月に開始します。<br /><br /> ビルド番号。|  
|ProductBuildType|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> 現在のビルドのビルドの種類です。<br /><br /> 次のいずれかを返します。<br /><br /> OD、特定の顧客にオンデマンドでリリースを = です。<br /><br /> GDR 一般配布リリースが windows update を介してリリースを = です。<br /><br /> NULL<br />= は適用されません。|  
|ProductLevel|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのバージョンのレベルです。<br /><br /> 次のいずれかを返します。<br /><br /> 'RTM' = オリジナル リリース バージョン<br /><br /> 'SP*n*' = サービス パック バージョン<br /><br /> ' CTP*n*'、Community Technology Preview バージョンを =<br /><br /> 基本データ型: **nvarchar (128)**|  
|ProductMajorVersion|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> メジャー バージョン。|  
|ProductMinorVersion|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> マイナー バージョン。|  
|ProductUpdateLevel|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> 現在のビルドのレベルを更新します。 CU では、累積更新プログラムを示します。<br /><br /> 次のいずれかを返します。<br /><br /> CU *n* 累積更新プログラムを =<br /><br /> NULL<br />= は適用されません。|  
|ProductUpdateReference|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]遅延 2015 以降で更新プログラムの現在のバージョンを使用します。<br /><br /> そのリリースのサポート技術情報の記事です。|  
|ProductVersion|インスタンスのバージョン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の形式で '*major.minor.build.revision*' です。<br /><br /> 基本データ型: **nvarchar (128)**|  
|ResourceLastUpdateDateTime|リソース データベースが最後に更新された日時を返します。<br /><br /> 基本データ型: **datetime**|  
|ResourceVersion|リソース データベースのバージョンを返します。<br /><br /> 基本データ型: **nvarchar (128)**|  
|ServerName|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスに関連付けられている Windows サーバーとインスタンスの情報。<br /><br /> NULL = 入力が無効、または、エラーが発生します。<br /><br /> 基本データ型: **nvarchar (128)**|  
|SqlCharSet|照合順序 ID の SQL 文字セット ID。<br /><br /> 基本データ型: **tinyint**|  
|SqlCharSetName|照合順序の SQL 文字セットの名前。<br /><br /> 基本データ型: **nvarchar (128)**|  
|SqlSortOrder|照合順序の SQL 並べ替え順序 ID。<br /><br /> 基本データ型: **tinyint**|  
|SqlSortOrderName|照合順序の SQL 並べ替え順序の名前。<br /><br /> 基本データ型: **nvarchar (128)**|  
|FilestreamShareName|FILESTREAM で使用される共有の名前。<br /><br /> NULL = 無効な入力、エラー、または該当なし|  
|FilestreamConfiguredLevel|FILESTREAM アクセスの構成されているレベル。 詳細については、次を参照してください。 [filestream アクセス レベル](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)です。|  
|FilestreamEffectiveLevel|FILESTREAM アクセスの有効なレベル。 レベルが変更されており、インスタンスの再起動またはコンピューターの再起動のいずれかが保留されている場合、この値は FilestreamConfiguredLevel と異なることがあります。 詳細については、次を参照してください。 [filestream アクセス レベル](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)です。|  
  
## <a name="return-types"></a>戻り値の型  
 **sql_variant**  
  
## <a name="remarks"></a>解説  
  
### <a name="servername-property"></a>ServerName プロパティ  
 `ServerName`のプロパティ、`SERVERPROPERTY`関数と[@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md)同様の情報を返します。 `ServerName` プロパティが返す Windows サーバーとインスタンス名を合わせることで、一意なサーバー インスタンスが形成されます。 [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md)現在構成されているローカル サーバー名を提供します。  
  
 `ServerName`プロパティおよび[@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md)インストール時に既定のサーバー名が変更されていない場合は、同じ情報を返します。 ローカル サーバー名は次のストアド プロシージャを実行することによって構成できます。  
  
```  
EXEC sp_dropserver 'current_server_name';  
GO  
EXEC sp_addserver 'new_server_name', 'local';  
GO  
```  
  
 ローカル サーバー名がインストール時に、既定のサーバー名から変更された場合[@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md)新しい名前を返します。  
  
### <a name="version-properties"></a>バージョンのプロパティ  
 `SERVERPROPERTY`一方、バージョン情報に関連する個々 のプロパティを返す関数、 [@@VERSION ](../../t-sql/functions/version-transact-sql-configuration-functions.md)関数は、1 つの文字列に出力を結合します。 使用することができます、アプリケーションは、個々 のプロパティ文字列を必要とする場合、`SERVERPROPERTY`解析ではなくを取得する関数、 [@@VERSION ](../../t-sql/functions/version-transact-sql-configuration-functions.md)結果。  

## <a name="permissions"></a>Permissions

すべてのユーザーには、サーバーのプロパティを照会できます。 
  
## <a name="examples"></a>使用例  
 次の例では、`SERVERPROPERTY`で機能、`SELECT`の現在のインスタンスに関する情報を返すステートメント[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。   
  
```  
SELECT  
  SERVERPROPERTY('MachineName') AS ComputerName,
  SERVERPROPERTY('ServerName') AS InstanceName,  
  SERVERPROPERTY('Edition') AS Edition,
  SERVERPROPERTY('ProductVersion') AS ProductVersion,  
  SERVERPROPERTY('ProductLevel') AS ProductLevel;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server 2016 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)  
  
  

