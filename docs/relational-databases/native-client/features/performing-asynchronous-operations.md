---
title: 非同期操作を実行する |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d3bd1ee2baf56a92068d58fffd783cd492609c71
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420491"
---
# <a name="performing-asynchronous-operations"></a>非同期操作の実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、アプリケーションは非同期のデータベース操作を実行できます。 非同期処理により、呼び出し側のスレッドをブロックしないで直ちに制御を返すことができるようになります。 これは、マルチスレッドの持つ能力と柔軟性を大きく引き出し、開発者が明示的にスレッドを作成したり、同期を処理する手間を省くことができる機能です。 アプリケーションは、データベース接続を初期化するときや、コマンドの実行結果を初期化するときに、非同期処理を要求します。  
  
## <a name="opening-and-closing-a-database-connection"></a>データベース接続の開閉  
 使用する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、データ ソース オブジェクトを非同期的に初期化するために設計されたアプリケーションを呼び出す前に DBPROP_INIT_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定できます**Idbinitialize::initialize**します。 プロバイダーを返しますへの呼び出しからすぐにこのプロパティを設定すると、**初期化**操作が、すぐに完了した場合は S_OK または DB_S_ASYNCHRONOUS、初期化が非同期に続行する場合のいずれかでします。 アプリケーションを照会できます、 **IDBAsynchStatus**または[ISSAsynchStatus](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)、データ ソース オブジェクトのインターフェイスを呼び出して**idbasynchstatus::getstatus**または[Issasynchstatus::waitforasynchcompletion](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)初期化の状態を取得します。  
  
 また、DBPROPSET_SQLSERVERROWSET プロパティ セットに SSPROP_ISSAsynchStatus プロパティが追加されています。 サポートするプロバイダー、 **ISSAsynchStatus**インターフェイスは、このプロパティを VARIANT_TRUE の値を実装する必要があります。  
  
 **Idbasynchstatus::abort**または[issasynchstatus:](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)非同期のキャンセルを呼び出すことができます**初期化**呼び出します。 コンシューマーは、明示的にデータ ソースの非同期の初期化を要求できます。 それ以外の場合、 **idbinitialize::initialize**データ ソース オブジェクトが完全に初期化されるまでは返されません。  
  
> [!NOTE]  
>  接続プールの使用されるデータ ソース オブジェクトを呼び出すことはできません、 **ISSAsynchStatus**インターフェイスで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー。 **ISSAsynchStatus**インターフェイスは、プールされたデータ ソース オブジェクトは公開されません。  
>   
>  アプリケーションが、カーソル エンジンの使用を明示的に強制する場合**iopenrowset::openrowset**と**imultipleresults::getresult**非同期処理ではサポートされません。  
>   
>  また、MDAC 2.8) の「リモート処理プロキシ/スタブの dll を呼び出すことはできません、 **ISSAsynchStatus**インターフェイスで[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client。 **ISSAsynchStatus**インターフェイスは、リモート処理は公開されません。  
>   
>  サービス コンポーネントをサポートしていない**ISSAsynchStatus**します。  
  
## <a name="execution-and-rowset-initialization"></a>実行と行セットの初期化  
 コマンドの実行結果を非同期に開くようデザインされているアプリケーションは、DBPROP_ROWSET_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定できます。 呼び出しの前にこのビットを設定するときに**idbinitialize::initialize**、 **icommand::execute**、 **iopenrowset::openrowset**または**IMultipleResults:。GetResult**、 *riid*引数を IID_IDBAsynchStatus、IID_ISSAsynchStatus、または IID_IUnknown に設定する必要があります。  
  
 メソッドを直ちに返しますは S_OK、行セットの初期化が完了するとすぐに、または DB_S_ASYNCHRONOUS を行セットは、非同期的に初期化が解決しない場合と*ppRowset*で要求されたインターフェイスに設定します行セット。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、このインターフェイスは、必ず**IDBAsynchStatus**または**ISSAsynchStatus**します。 一時停止状態と呼び出しを使用した場合、このインターフェイスの動作、行セットが完全に初期化されるまで**QueryInterface**以外のインターフェイスに対して**IID_IDBAsynchStatus**または**iid _ISSAsynchStatus** E_NOINTERFACE を返す可能性があります。 コンシューマーが明示的に非同期処理を要求しない限り、行セットは同期的に初期化されます。 要求されたすべてのインターフェイスには**idbasynchstaus:** または**issasynchstatus::waitforasynchcompletion**し非同期操作が完了したことを示すを返します。 これは、必ずしも行セットに完全にデータが格納されたことを意味するものではありませんが、行セットは完成し、完全に機能します。  
  
 実行されたコマンドが行セットを返さない場合、まだを直ちに返しますをサポートするオブジェクト**IDBAsynchStatus**します。  
  
 非同期コマンドの実行により複数の結果を取得する必要がある場合は、次の操作を行います。  
  
-   コマンドを実行する前に、DBPROP_ROWSET_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定します。  
  
-   呼び出す**icommand::execute**、および要求**IMultipleResults**します。  
  
 **IDBAsynchStatus**と**ISSAsynchStatus**インターフェイス複数結果インターフェイスを使用して、クエリを実行して取得できます**QueryInterface**します。  
  
 コマンドの実行が完了時に**IMultipleResults** 、同期操作のケースから 1 つの例外は、通常どおり使用できます: DB_S_ASYNCHRONOUS が返される、後者**IDBAsynchStatus**または**ISSAsynchStatus**操作が完了したかを判断するために使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、アプリケーションが非ブロッキング メソッドを呼び出し、いくつか他の処理を実行し、制御を戻して結果を処理します。 **Issasynchstatus::waitforasynchcompletion** 、非同期実行操作が完了するまで、内部イベント オブジェクト上で指定された時間待機*dwMilisecTimeOut*が渡されます。  
  
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
  
 **Issasynchstatus::waitforasynchcompletion** 、非同期実行操作が完了するまで、内部イベント オブジェクトを待機または*dwMilisecTimeOut*値が渡されます。  
  
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
 [ISSAsynchStatus &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
