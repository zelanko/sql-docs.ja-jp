---
title: 複数のアクティブな結果セット (MARS) を使用して |Microsoft Docs
description: 複数のアクティブな結果セット (MARS) の使用
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, MARS
- MSOLEDBSQL, MARS
- data access [OLE DB Driver for SQL Server], MARS
- Multiple Active Result Sets
- OLE DB Driver for SQL Server, MARS
- MARS [SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 7f0c8c9d13eca087db3d7202d57c058527e2c073
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610320"
---
# <a name="using-multiple-active-result-sets-mars"></a>複数のアクティブな結果セット (MARS) の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、[!INCLUDE[ssDE](../../../includes/ssde-md.md)] にアクセスするアプリケーションで複数のアクティブな結果セット (MARS) がサポートされるようになりました。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、データベース アプリケーションは 1 つの接続で複数のアクティブなステートメントを保持できませんでした。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定の結果セットを使用しているときは、アプリケーションはその接続で他のバッチを実行する前に、1 つのバッチのすべての結果セットを処理するか、取り消す必要がありました。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では新しい接続属性が導入され、アプリケーションは接続ごとに複数の要求を保留中にできるだけでなく、接続ごとに複数のアクティブな既定の結果セットを保持できるようになりました。  
  
 MARS によって、次の新しい機能を使用したアプリケーションのデザインが簡素化されます。  
  
-   アプリケーションは、既定の結果セットを複数開くことができ、複数の既定の結果セットからの読み取りをインターリーブすることができます。  
  
-   アプリケーションは既定の結果セットを開いたまま、他のステートメント (INSERT、UPDATE、DELETE、ストアド プロシージャ呼び出しなど) を実行できます。  
  
 MARS を使用するアプリケーションについては、次のガイドラインを参照してください。  
  
-   1 つの SQL ステートメント (SELECT、OUTPUT を伴う DML、RECEIVE、READ TEXT など) で生成される結果セットが短期間しか有効でない場合や結果セットが小さい場合は、既定の結果セットを使用します。  
  
-   1 つの SQL ステートメントで生成される結果セットが長期間有効な場合や結果セットが大きくなる場合は、サーバー カーソルを使用します。  
  
-   結果を返すかどうかにかかわらず手続き型の要求の場合、および複数の結果を返すバッチの場合、常に、結果の最後まで読み取ります。  
  
-   接続プロパティの変更やトランザクションの管理には、できるだけ [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントではなく API 呼び出しを優先して使用します。  
  
-   MARS では、複数のバッチが同時に実行されている間、セッション スコープの権限の借用が禁止されます。  
  
> [!NOTE]  
>  既定では、MARS 機能は有効になっていません。 接続するときに、MARS を使用する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]OLE DB Driver for SQL Server を使用する必要があります具体的には有効にする接続文字列内で。 詳細については、OLE DB Driver for SQL Server セクションでは、このトピックの後半を参照してください。  
  
 OLE DB Driver for SQL Server では、接続でアクティブなステートメントの数は制限されません。  
  
 複数のステートメントで構成される単一のバッチやストアド プロシージャを複数同時実行する必要のない一般的なアプリケーションでは、MARS の実装方法を理解しなくても、MARS の利点を得ることができます。 ただし、より複雑な要件のアプリケーションでは、MARS の実装方法を考慮する必要があります。  
  
 MARS では、1 つの接続内で複数の要求の実行をインターリーブできます。 つまり、1 つのバッチを実行し、その実行内で他の要求を実行できます。 ただし、MARS では並列実行が行われるのではなく、複数の実行がインターリーブされることに注意してください。  
  
 MARS のインフラストラクチャでは、複数のバッチがインターリーブ方式で実行されますが、実行の切り替えは明確に定義された時点でしか行われません。 また、ほとんどのステートメントはバッチ内で自動的に実行される必要があります。 クライアントに行を返すステートメント ("*呼び出しポイント*" と呼ばれることもあります) では、行をクライアントへ送信しているとき、その送信を完了する前に実行をインターリーブすることができます。次に例を示します。  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 ストアド プロシージャまたはバッチの一部として実行されるその他のステートメントはいずれも、他の MARS 要求に切り替えられる前に実行を完了する必要があります。  
  
 バッチがどのようにインターリーブ実行されるかは、さまざまな要因の影響を受けます。そのため、呼び出しポイントを含む複数のバッチからのコマンドが実行されるときに、正確なシーケンスを予測することは困難です。 このような複雑なバッチをインターリーブ実行したときに、好ましくない影響が発生しないように注意してください。  
  
 このような問題を回避するために、接続状態 (SET、USE) やトランザクション (BEGIN TRAN、COMMIT、ROLLBACK) を管理する場合は、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントではなく API 呼び出しを使用します。このとき、複数のステートメントで構成されるバッチに呼び出しポイントも含まれている場合、接続状態やトランザクションを管理するステートメントを含めないようにします。さらに、このようなバッチでは、すべての結果を処理するか、残りを取り消すことによって、実行を順番に行います。  
  
> [!NOTE]  
>  MARS が有効なときにトランザクションを手動または暗黙に開始するバッチやストアド プロシージャでは、バッチが終了する前にトランザクションを完了する必要があります。 トランザクションを完了しないと、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はバッチの終了時にトランザクションによって行われたすべての変更をロールバックします。 このようなトランザクションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によってバッチスコープのトランザクションとして管理されます。 これは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入された新しい形式のトランザクションで、MARS が有効なときに、既存の適切に動作するストアド プロシージャを使用できるようになります。 バッチ スコープのトランザクションの詳細については、次を参照してください。[トランザクション ステートメント&#40;TRANSACT-SQL&#41;](../../../t-sql/statements/statements.md)します。  
  
 ADO から MARS を使用しての例は、次を参照してください。 [OLE DB Driver for SQL Server で使用する ADO](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md)します。  
  
## <a name="in-memory-oltp"></a>インメモリ OLTP  
 インメモリ OLTP では、クエリを使用して MARS をサポートし、ネイティブ コンパイル ストアド プロシージャ。 MARS では、完全に新しい結果セットから行をフェッチする要求を送信する前に設定する各結果を取得することがなく複数のクエリからデータを要求できるようにします。 複数の開いている結果セットから正常に読み取られた、MARS が有効になっている接続を使用する必要があります。  
  
 追加することで明示的に有効にする必要がありますので、既定で MARS が無効に`MultipleActiveResultSets=True`接続文字列にします。 次の例では、SQL Server のインスタンスに接続し、MARS が有効になっていることを指定する方法を示します。  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS、インメモリ OLTP では、基本的に MARS と同じ SQL エンジンの残りの部分で。 次に示します MARS を使用してメモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャとの相違点を。  
  
 **MARS とメモリ最適化テーブル**  
  
 次に、ディスク ベースおよびメモリ最適化テーブルを MARS を使用して接続を有効にした場合の違いを示します。  
  
-   書き込み-書き込みの競合する新しい操作が失敗すると、同じレコードを変更しようとすると、両方は 2 つのステートメントが同じターゲット オブジェクトにデータを変更できます。 ただし、両方の操作では、別のレコードを変更する場合、操作は成功します。  
  
-   各ステートメントは、新しい操作が既存のステートメントによって行われた変更を確認できませんように、スナップショット分離下で実行されます。 同じトランザクションで同時実行のステートメントが実行された場合でも、SQL エンジンはバッチ スコープのトランザクションの各ステートメントに対して互いに独立したを作成します。 ただし、ため、1 つのバッチ スコープのトランザクションのロールバックに同じバッチ内の他の影響を与えます、バッチ スコープのトランザクションが結合されてもいます。  
  
-   すぐに障害になるために、ユーザー トランザクションに DDL 操作は許可されていません。  
  
 **MARS およびネイティブ コンパイル ストアド プロシージャ**  
  
 ネイティブ コンパイル ストアド プロシージャでは、MARS を有効になっている接続でを実行し、yield ポイントが発生した場合にのみ、別のステートメントの実行を生成できます。 Yield ポイントでは、SELECT ステートメントを別のステートメントの実行が明け渡さできますをネイティブ コンパイル ストアド プロシージャ内の唯一のステートメントである必要があります。 SELECT ステートメントが生成しない手順では存在しない場合は、他のステートメントの開始前に完了するまで実行されます。  
  
 **MARS とインメモリ OLTP でのトランザクション**  
  
 ステートメントとはインターリーブされます。 atomic ブロックによって行われた変更は、互いから分離されます。 たとえば、1 つのステートメントまたは atomic ブロックは、いくつかの変更を行い、別のステートメントの実行が生成される場合、新しいステートメントは最初のステートメントによって行われた変更は表示されません。 さらに、最初のステートメントが実行を再開時に他のステートメントによって加えられた変更しない表示されます。 ステートメントは、終了され、ステートメントが開始する前にコミットされる変更にのみ表示されます。  
  
 新しいユーザー トランザクションは、BEGIN TRANSACTION ステートメントを使用して現在のユーザー トランザクション内で開始できます – これは、相互運用モードでのみサポートされているため、BEGIN TRANSACTION は、T-SQL ステートメントからのみ呼び出すことされからネイティブ コンパイルで保存されません。プロシージャです。 保存を作成する保存トランザクションまたはトランザクションへの API 呼び出しを使用してトランザクションにポイントします。セーブポイントにロールバックする Save(save_point_name) します。 この機能は、T-SQL ステートメントからのみ有効になりますからではなく内でネイティブ コンパイル ストアド プロシージャ。  
  
 **MARS と列ストア インデックス**  
  
 SQL Server (2016年以降) では、列ストア インデックスで MARS をサポートしています。 SQL Server 2014 では、列ストア インデックスに読み取り専用で接続するために MARS が使用されます。    ただし、SQL Server 2014 では、列ストア インデックスを含むテーブルで DML (データ操作言語) を同時操作するとき、MARS を利用できません。 その場合、SQL Server は接続を強制終了し、トランザクションを中止します。   SQL Server 2012 は読み取り専用の列ストア インデックスを備え、MARS は、それらには適用されません。  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server  
 OLE DB Driver for SQL Server では、DBPROPSET_SQLSERVERDBINIT プロパティ セットに実装される SSPROP_INIT_MARSCONNECTION データ ソース初期化プロパティの追加によって、MARS がサポートされます。 また、新しい接続文字列のキーワードとして **MarsConn** が追加されました。 受け取って**true**または**false**値。**false**既定値です。  
  
 データ ソース プロパティ DBPROP_MULTIPLECONNECTIONS の既定値は VARIANT_TRUE です。 これは、複数の同時実行コマンドや行セット オブジェクトをサポートするために、プロバイダーが複数の接続を起動することを意味しています。 MARS が有効なとき、OLE DB Driver for SQL Server では 1 つの接続で複数のコマンドや行セット オブジェクトをサポートできるので、MULTIPLE_CONNECTIONS が既定で VARIANT_FALSE に設定されます。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットに加えられた機能強化の詳細については、次を参照してください。[初期化プロパティと承認プロパティ](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)します。  
  
### <a name="ole-db-driver-for-sql-server-example"></a>OLE DB Driver for SQL Server の例  
 次の例では、セッション オブジェクトを作成する前に、OLE DB Driver for SQL Server を使用してデータ ソース オブジェクトを作成し、DBPROPSET_SQLSERVERDBINIT プロパティ セットを使用して MARS を有効にしています。  
  
```  
#include <msoledbsql.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  

  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 
  
  
