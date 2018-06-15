---
title: 非同期操作を実行する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|features
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1b433851601bb3bbe1a9bd339b4af2b0835c1673
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32953267"
---
# <a name="performing-asynchronous-operations"></a>非同期操作の実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、アプリケーションは非同期のデータベース操作を実行できます。 非同期処理により、呼び出し側のスレッドをブロックしないで直ちに制御を返すことができるようになります。 これは、マルチスレッドの持つ能力と柔軟性を大きく引き出し、開発者が明示的にスレッドを作成したり、同期を処理する手間を省くことができる機能です。 アプリケーションは、データベース接続を初期化するときや、コマンドの実行結果を初期化するときに、非同期処理を要求します。  
  
## <a name="opening-and-closing-a-database-connection"></a>データベース接続の開閉  
 使用する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、データ ソース オブジェクトを非同期的に初期化するために設計されたアプリケーションは呼び出しの前に DBPROP_INIT_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定できます**Idbinitialize::initialize**です。 プロバイダーを返しますへの呼び出しからすぐにこのプロパティを設定すると、**初期化**での操作が直ちに、完了した場合は S_OK、または初期化が非同期に続行される場合は DB_S_ASYNCHRONOUS します。 アプリケーションを照会できます、 **IDBAsynchStatus**または[ISSAsynchStatus](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)データ ソース オブジェクトのインターフェイスを呼び出す**idbasynchstatus::getstatus**または[Issasynchstatus::waitforasynchcompletion](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)初期化のステータスを取得します。  
  
 また、DBPROPSET_SQLSERVERROWSET プロパティ セットに SSPROP_ISSAsynchStatus プロパティが追加されています。 サポートするプロバイダー、 **ISSAsynchStatus**インターフェイスが VARIANT_TRUE の値は、このプロパティを実装する必要があります。  
  
 **Idbasynchstatus::abort**または[issasynchstatus::abort](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)非同期のキャンセルを呼び出すことができる**初期化**呼び出します。 コンシューマーは、明示的にデータ ソースの非同期の初期化を要求できます。 それ以外の場合、 **idbinitialize::initialize**データ ソース オブジェクトが完全に初期化されるまで返されません。  
  
> [!NOTE]  
>  接続プールを使用するデータ ソース オブジェクトを呼び出すことはできません、 **ISSAsynchStatus**インターフェイスで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。 **ISSAsynchStatus**プールされているデータ ソース オブジェクトのインターフェイスは公開されません。  
>   
>  場合は、アプリケーションが明示的にカーソル エンジンの使用を強制**iopenrowset::openrowset**と**imultipleresults::getresult**は非同期処理をサポートしていません。  
>   
>  さらのリモート処理プロキシ/スタブの dll (MDAC 2.8) を呼び出すことはできません、 **ISSAsynchStatus**インターフェイスで[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client です。 **ISSAsynchStatus**インターフェイスは、リモート処理は公開されません。  
>   
>  サービス コンポーネントをサポートしていない**ISSAsynchStatus**です。  
  
## <a name="execution-and-rowset-initialization"></a>実行と行セットの初期化  
 コマンドの実行結果を非同期に開くようデザインされているアプリケーションは、DBPROP_ROWSET_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定できます。 呼び出しの前にこのビットを設定するときに**idbinitialize::initialize**、 **icommand::execute**、 **iopenrowset::openrowset**または**IMultipleResults:。GetResult**、 *riid*引数を IID_IDBAsynchStatus、IID_ISSAsynchStatus、または IID_IUnknown に設定する必要があります。  
  
 メソッドは S_OK をすぐに返します行セットの初期化が完了した場合、すぐにまたは db_s_asynchronous を返して、行セットは、非同期的に初期化が解決しない場合に*ppRowset*で要求されたインターフェイスへの設定、行セット。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、このインターフェイスは、必ず**IDBAsynchStatus**または**ISSAsynchStatus**です。 このインターフェイスが一時停止状態と呼び出し元にした場合と同じ動作は、行セットが完全に初期化されるまで**QueryInterface**以外のインターフェイスに対して**IID_IDBAsynchStatus**または**iid _ISSAsynchStatus** E_NOINTERFACE を返す可能性があります。 コンシューマーが明示的に非同期処理を要求しない限り、行セットは同期的に初期化されます。 要求されたすべてのインターフェイスは、使用可能な場合に**idbasynchstaus:** または**issasynchstatus::waitforasynchcompletion**非同期操作が完了したことを示す値を返します。 これは、必ずしも行セットに完全にデータが格納されたことを意味するものではありませんが、行セットは完成し、完全に機能します。  
  
 実行されたコマンドが行セットを返さない場合も直ちにを返したをサポートするオブジェクト**IDBAsynchStatus**です。  
  
 非同期コマンドの実行により複数の結果を取得する必要がある場合は、次の操作を行います。  
  
-   コマンドを実行する前に、DBPROP_ROWSET_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定します。  
  
-   呼び出す**icommand::execute**、および要求**IMultipleResults**です。  
  
 **IDBAsynchStatus**と**ISSAsynchStatus**インターフェイス、複数の結果を使用してインターフェイスを照会して取得できます**QueryInterface**です。  
  
 コマンドの実行が完了時に**IMultipleResults**通常、同期のケースから 1 つの例外として使用できます: DB_S_ASYNCHRONOUS が返されます、後者**IDBAsynchStatus**または**ISSAsynchStatus**操作が完了するために使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、アプリケーションが非ブロッキング メソッドを呼び出し、いくつか他の処理を実行し、制御を戻して結果を処理します。 **Issasynchstatus::waitforasynchcompletion** 、非同期実行操作が完了するまで、内部イベント オブジェクトまたはで指定された時間を待機*dwMilisecTimeOut*が渡されます。  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 **Issasynchstatus::waitforasynchcompletion** 、非同期実行操作が完了するまで、内部イベント オブジェクトのハンドルを待機または*dwMilisecTimeOut*値が渡されます。  
  
 次の例は、複数の結果セットを返す非同期処理のコードです。  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 ブロックを防ぐため、次の例のように、クライアントでは実行中の非同期操作の状態を確認できます。  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 次の例は、現在実行中の非同期操作を中止する方法を示しています。  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [行セットのプロパティと動作](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [ISSAsynchStatus (&) #40";"OLE DB"&"#41;](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
