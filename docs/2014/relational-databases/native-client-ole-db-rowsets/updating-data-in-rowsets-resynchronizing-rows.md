---
title: 行の再同期 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b041dc07afb30fff0c03d96fec9cd8a5d62f965
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63229010"
---
# <a name="resynchronizing-rows"></a>行の再同期
  Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、カーソルが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サポートされている行セットに対してのみ**IRowsetResynch**をサポートします。 **IRowsetResynch**は、オンデマンドでは利用できません。 コンシューマーは、行セットを開く前にインターフェイスを要求する必要があります。  
  
## <a name="see-also"></a>参照  
 [行セット内のデータの更新](updating-data-in-rowsets.md)  
  
  
