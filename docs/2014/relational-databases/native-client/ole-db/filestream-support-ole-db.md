---
title: FILESTREAM のサポート (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad6aa7b55906e68dba6615140ef2c6afcc3efaa5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62668935"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM のサポート (OLE DB)
  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]および[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 以降では、OLE DB では、拡張された FILESTREAM 機能がサポートされています。 この機能の詳細については、「 [FILESTREAM のサポート](../features/filestream-support.md)」を参照してください。 サンプルについては、「[FILESTREAM と OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)」を参照してください。  
  
 アプリケーションで 2 GB より大きい `varbinary(max)` 値を送受信するには、パラメーターと結果のバインドで `DBTYPE_IUNKNOWN` を使用します。 パラメーターの場合、プロバイダーは ISequentialStream および ISequentialStream を返す結果に対して IUnknown::QueryInterface を呼び出す必要があります。  
  
 OLE DB の場合は、ISequentialStream 値に関連するチェックが緩和されます。 *Wtype*が`DBTYPE_IUNKNOWN` `DBBINDING`構造体に含まれている場合は、 *dwpart*から`DBPART_LENGTH`を省略するか、データの長さ (データバッファー内のオフセット*oblength* ) を ~ 0 に設定することによって、長さのチェックを無効にすることができます。 この場合、プロバイダーは値の長さをチェックせず、ストリームで利用可能なすべてのデータを要求し、返します。 この変更は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (以降の) サーバーに接続する場合に限り、すべてのラージ オブジェクト (LOB) 型と XML に適用されます。 これにより、既存のアプリケーションや下位レベルのサーバーとの一貫性や下位互換性を維持しつつ、より柔軟な開発が可能になります。  
  
 この変更は、データを転送するすべてのインターフェイス (主に IRowset:: GetData、ICommand:: Execute、および IRowsetFastLoad::InsertRow) に影響します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../sql-server-native-client-programming.md)  
  
  
