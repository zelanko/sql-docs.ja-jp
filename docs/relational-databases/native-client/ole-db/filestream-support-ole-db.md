---
title: FILESTREAM のサポート (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
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
ms.openlocfilehash: ad287aad1d87310a93bb2917d889775bba1e0650
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420011"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM のサポート (OLE DB)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  以降で[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0、OLE DB は、強化された FILESTREAM 機能をサポートしています。 この機能の詳細については、次を参照してください。 [FILESTREAM のサポート](../../../relational-databases/native-client/features/filestream-support.md)します。 サンプルについては、次を参照してください。 [Filestream と OLE DB](../../../relational-databases/native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)します。  
  
 送受信する**varbinary (max)** 2 GB より大きい値では、アプリケーションを使用して**DBTYPE_IUNKNOWN**パラメーターと結果のバインドにします。 パラメーターのプロバイダーは ISequentialStream と ISequentialStream を返す結果の iunknown::queryinterface を呼び出す必要があります。  
  
 OLE DB の ISequentialStream 値に関連するチェックが緩和されます。 ときに*wType*は**DBTYPE_IUNKNOWN**で、 **DBBINDING**構造体、長さのチェック、省略するか無効になっている**DBPART_LENGTH***dwPart*またはデータの長さを設定して (オフセット*obLength*データ バッファー内) に ~ 0。 この場合、プロバイダーは値の長さをチェックせず、ストリームで利用可能なすべてのデータを要求し、返します。 この変更は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (以降の) サーバーに接続する場合に限り、すべてのラージ オブジェクト (LOB) 型と XML に適用されます。 これにより、既存のアプリケーションや下位レベルのサーバーとの一貫性や下位互換性を維持しつつ、より柔軟な開発が可能になります。  
  
 この変更では、irowset::getdata、icommand::execute、および irowsetfastload::insertrow 主のデータを転送するすべてのインターフェイスに影響します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
