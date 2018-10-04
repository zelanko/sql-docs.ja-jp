---
title: ISSAbort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4b3e43dca5a18a991733492eeeffc4f49d14ef8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181242"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  **ISSAbort**で公開される、インターフェイス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、提供、 [issabort::abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)現在の行セットと任意のコマンドをキャンセルするために使用するメソッドがバッチ処理最初に、行セットを生成してをまだ完了していない実行コマンド。  
  
 **ISSAbort**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client プロバイダーに固有のインターフェイスを使用して利用可能な**QueryInterface**上、 **IMultipleResults**によって返されるオブジェクト**Icommand::execute**または**iopenrowset::openrowset**します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|説明|  
|------------|-----------------|  
|[Issabort::abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
