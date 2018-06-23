---
title: ISSAbort (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 53c6e2c7c06331ce75883f86a8935d4d1c2419c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075781"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  **ISSAbort**が公開するインターフェイス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider では、 [issabort::abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)を現在の行セットとどのようなコマンドを取り消すために使用するメソッドがバッチ処理コマンドを使用してを最初に生成された行セット、およびをまだ完了していない実行します。  
  
 **ISSAbort**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client プロバイダーに固有のインターフェイスを使用して利用可能な**QueryInterface**上、 **IMultipleResults**によって返されるオブジェクト**Icommand::execute**または**iopenrowset::openrowset**です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|説明|  
|------------|-----------------|  
|[Issabort::abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  