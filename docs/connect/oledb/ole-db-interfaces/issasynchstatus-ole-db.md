---
title: ISSAsynchStatus (OLE DB) |Microsoft ドキュメント
description: ISSAsynchStatus (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 73ee8ab77cab188cf4a3d0d98c5dc1f238c8e3f0
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689095"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **ISSAsynchStatus**インターフェイスのサポートが公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]非同期操作です。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**IDBAsynchStatus**です。 加え、**中止**と**GetStatus**から継承されたメソッド**IDBAsynchStatus**、 **ISSAsynchStatus** 1 つの新しいメソッドを提供します。非同期操作が完了したか、タイムアウトが発生するまで待機するを使用します。  
  
|方法|説明|  
|------------|-----------------|  
|[Issasynchstatus::abort &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-abort-ole-db.md)|非同期に実行されている操作を取り消します。|  
|[Issasynchstatus::getstatus &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|非同期に実行されている操作の状態を返します。|  
|[Issasynchstatus::waitforasynchcompletion &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|非同期に実行されている操作が完了するかタイムアウトが発生するまで待機します。|  
  
## <a name="remarks"></a>コメント  
 **ISSAsynchStatus**の実装、 **issasynchstatus::getstatus**メソッドと同じ、 **idbasynchstatus::getstatus**似ているが、メソッド、データ ソース オブジェクトの初期化が中止されると、E_UNEXPECTED が返される DB_E_CANCELED ではなく (ただし**issasynchstatus::waitforasynchcompletion** DB_E_CANCELED が返されます)。 データ ソース オブジェクトされていない状態で残るため、通常中止操作では、次の追加の初期化操作が試行されることをお勧めします。  
  
 次に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の非同期実行の使用をサポートしているメソッドを示します。  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [非同期操作の実行](../../oledb/features/performing-asynchronous-operations.md)  
  
  
