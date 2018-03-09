---
title: "ISSAsynchStatus (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords: ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
caps.latest.revision: "33"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9055e0410deed0d77c1bf14554789e753d229ef7
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ISSAsynchStatus**のサポートが公開[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非同期操作です。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**IDBAsynchStatus**です。 加え、**中止**と**GetStatus**から継承されたメソッド**IDBAsynchStatus**、 **ISSAsynchStatus** 1 つの新しいメソッドを提供します。非同期操作が完了したか、タイムアウトが発生するまで待機するを使用します。  
  
|方法|Description|  
|------------|-----------------|  
|[Issasynchstatus::abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)|非同期に実行されている操作を取り消します。|  
|[Issasynchstatus::getstatus &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|非同期に実行されている操作の状態を返します。|  
|[Issasynchstatus::waitforasynchcompletion &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|非同期に実行されている操作が完了するかタイムアウトが発生するまで待機します。|  
  
## <a name="remarks"></a>解説  
 **ISSAsynchStatus**の実装、 **issasynchstatus::getstatus**メソッドと同じ、 **idbasynchstatus::getstatus**似ているが、メソッド、データ ソース オブジェクトの初期化が中止されると、E_UNEXPECTED が返される DB_E_CANCELED ではなく (ただし**issasynchstatus::waitforasynchcompletion** DB_E_CANCELED が返されます)。 これは、初期化の中止後、追加の初期化操作が試行される場合に備えて、データ ソース オブジェクトの状態が通常の状態のままにならないためです。  
  
 次に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の非同期実行の使用をサポートしているメソッドを示します。  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [非同期操作の実行](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
