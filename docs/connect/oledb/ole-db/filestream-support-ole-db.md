---
title: FILESTREAM のサポート (OLE DB) |Microsoft ドキュメント
description: FILESTREAM のサポート (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7b1670cdda78f096ef776e7527910e71617c340
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="filestream-support-ole-db"></a>FILESTREAM のサポート (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  以降で[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]OLE DB Driver for SQL Server、OLE DB は、強化された FILESTREAM 機能をサポートしているとします。 この機能の詳細については、次を参照してください。 [FILESTREAM のサポート](../../oledb/features/filestream-support.md)です。 サンプルについては、次を参照してください。 [Filestream と OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md)です。  
  
 送信および受信する**varbinary (max)** 2 GB より大きい値では、アプリケーションを使用して**DBTYPE_IUNKNOWN**パラメーターと結果のバインドにします。 パラメーターのプロバイダーは ISequentialStream および ISequentialStream を返す結果の iunknown::queryinterface を呼び出す必要があります。  
  
 OLE DB の ISequentialStream 値に関連するチェックが緩和されます。 ときに*wType*は**DBTYPE_IUNKNOWN**で、 **DBBINDING**構造体、長さのチェックできる省略するか無効になっている**DBPART_LENGTH***dwPart*またはデータの長さを設定して (オフセット*obLength*データ バッファー内) に ~ 0 です。 この場合、プロバイダーは値の長さをチェックせず、ストリームで利用可能なすべてのデータを要求し、返します。 この変更は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (以降の) サーバーに接続する場合に限り、すべてのラージ オブジェクト (LOB) 型と XML に適用されます。 これにより、既存のアプリケーションや下位レベルのサーバーとの一貫性や下位互換性を維持しつつ、より柔軟な開発が可能になります。  
  
 この変更では、データ、irowset::getdata、icommand::execute、および irowsetfastload::insertrow 主に転送されるすべてのインターフェイスに影響します。  
  
## <a name="see-also"></a>参照  
 [SQL Server プログラミング用の OLE DB ドライバー](../../oledb/oledb-driver-for-sql-server-programming.md)  
  
  
