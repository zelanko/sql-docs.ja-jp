---
title: ISSAsynchStatus (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a67b1efda62d76bd947dcbc9291f47be7f5f907d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072110"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
  **ISSAsynchStatus**のサポートが公開[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非同期操作です。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**IDBAsynchStatus**です。 加え、**中止**と**GetStatus**から継承されたメソッド**IDBAsynchStatus**、 **ISSAsynchStatus** 1 つの新しいメソッドを提供します。非同期操作が完了したか、タイムアウトが発生するまで待機するを使用します。  
  
|方法|説明|  
|------------|-----------------|  
|[Issasynchstatus::abort &#40;OLE DB&#41;](issasynchstatus-abort-ole-db.md)|非同期に実行されている操作を取り消します。|  
|[Issasynchstatus::getstatus &#40;OLE DB&#41;](issasynchstatus-getstatus-ole-db.md)|非同期に実行されている操作の状態を返します。|  
|[Issasynchstatus::waitforasynchcompletion &#40;OLE DB&#41;](issasynchstatus-waitforasynchcompletion-ole-db.md)|非同期に実行されている操作が完了するかタイムアウトが発生するまで待機します。|  
  
## <a name="remarks"></a>コメント  
 **ISSAsynchStatus**の実装、 **issasynchstatus::getstatus**メソッドと同じ、 **idbasynchstatus::getstatus**似ているが、メソッド、データ ソース オブジェクトの初期化が中止されると、E_UNEXPECTED が返される DB_E_CANCELED ではなく (ただし**issasynchstatus::waitforasynchcompletion** DB_E_CANCELED が返されます)。 これは、初期化の中止後、追加の初期化操作が試行される場合に備えて、データ ソース オブジェクトの状態が通常の状態のままにならないためです。  
  
 次に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の非同期実行の使用をサポートしているメソッドを示します。  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [非同期操作の実行](../native-client/features/performing-asynchronous-operations.md)  
  
  