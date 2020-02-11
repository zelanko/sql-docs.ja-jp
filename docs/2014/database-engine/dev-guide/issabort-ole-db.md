---
title: ISSAbort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 801eb84df08837ec8e49b6bb0e28fc1f1115e674
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781038"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  **Issabort**インターフェイスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーで公開されています。 [Issabort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)メソッドを使用して、現在の行セットを取り消すために使用されます。また、行セットを最初に生成したコマンドを使用してバッチ処理されたコマンドと、まだ実行が完了していないコマンドを取り消します。  
  
 **Issabort**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ICommand:: Execute**または**IOpenRowset:: OpenRowset**によって返される**IMultipleResults**オブジェクトに対して**QueryInterface**を使用して使用可能な Native Client プロバイダー固有のインターフェイスです。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|[説明]|  
|------------|-----------------|  
|[ISSAbort:: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
