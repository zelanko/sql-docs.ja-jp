---
title: FILESTREAM のサポート (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3f249e7a7a6b48bad3a83533f903987b957d027
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913054"
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
  
  
