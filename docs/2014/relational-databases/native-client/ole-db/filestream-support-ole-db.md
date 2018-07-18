---
title: FILESTREAM のサポート (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 925c624139e64b5d3aeb371e5eaf70b0fa1da171
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416961"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM のサポート (OLE DB)
  以降で[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0、OLE DB は、強化された FILESTREAM 機能をサポートしています。 この機能の詳細については、次を参照してください。 [FILESTREAM のサポート](../features/filestream-support.md)します。 サンプルについては、次を参照してください。 [Filestream と OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)します。  
  
 アプリケーションで 2 GB より大きい `varbinary(max)` 値を送受信するには、パラメーターと結果のバインドで `DBTYPE_IUNKNOWN` を使用します。 パラメーターのプロバイダーは ISequentialStream と ISequentialStream を返す結果の iunknown::queryinterface を呼び出す必要があります。  
  
 OLE DB の ISequentialStream 値に関連するチェックが緩和されます。 ときに*wType*は`DBTYPE_IUNKNOWN`で、`DBBINDING`構造体、長さをチェックすることができます省略するか無効になっている`DBPART_LENGTH`から*dwPart*か、または (オフセットでデータの長さを設定*obLength*データ バッファー内) に ~ 0。 この場合、プロバイダーは値の長さをチェックせず、ストリームで利用可能なすべてのデータを要求し、返します。 この変更は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (以降の) サーバーに接続する場合に限り、すべてのラージ オブジェクト (LOB) 型と XML に適用されます。 これにより、既存のアプリケーションや下位レベルのサーバーとの一貫性や下位互換性を維持しつつ、より柔軟な開発が可能になります。  
  
 この変更では、irowset::getdata、icommand::execute、および irowsetfastload::insertrow 主のデータを転送するすべてのインターフェイスに影響します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../sql-server-native-client-programming.md)  
  
  
