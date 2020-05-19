---
title: ISSAsynchStatus (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a4ea32cc0b36f1151c68b06af8f5445d4d46267b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704827"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
  **ISSAsynchStatus**は、非同期操作のサポートを公開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。 これは、コア OLE DB インターフェイス**id**から継承される省略可能なインターフェイスです。 **ISSAsynchStatus** には、**IDBAsynchStatus** から継承される **Abort** メソッドと **GetStatus** メソッドに加えて、非同期操作が完了するかタイムアウトが発生するまで待機する際に使用する新しいメソッドが 1 つ用意されています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort &#40;OLE DB&#41;](issasynchstatus-abort-ole-db.md)|非同期に実行されている操作を取り消します。|  
|[ISSAsynchStatus::GetStatus &#40;OLE DB&#41;](issasynchstatus-getstatus-ole-db.md)|非同期に実行されている操作の状態を返します。|  
|[ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;](issasynchstatus-waitforasynchcompletion-ole-db.md)|非同期に実行されている操作が完了するかタイムアウトが発生するまで待機します。|  
  
## <a name="remarks"></a>解説  
 **ISSAsynchStatus** に実装される **ISSAsynchStatus::GetStatus** メソッドは、**IDBAsynchStatus::GetStatus** メソッドと同じです。ただし、データ ソース オブジェクトの初期化が中止された場合、DB_E_CANCELED ではなく E_UNEXPECTED が返される点が異なります (**ISSAsynchStatus::WaitForAsynchCompletion** は、DB_E_CANCELED を返します)。 これは、初期化の中止後、追加の初期化操作が試行される場合に備えて、データ ソース オブジェクトの状態が通常の状態のままにならないためです。  
  
 次に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の非同期実行の使用をサポートしているメソッドを示します。  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [非同期操作の実行](../native-client/features/performing-asynchronous-operations.md)  
  
  
