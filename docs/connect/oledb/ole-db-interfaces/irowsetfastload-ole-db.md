---
title: IRowsetFastLoad (OLE DB) |Microsoft ドキュメント
description: IRowsetFastLoad (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18279d27c1beb7bf81e61adb901b41cedf3aa47b
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IRowsetFastLoad**インターフェイスのサポートが公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]メモリベースの一括コピー操作します。 OLE DB ドライバーの SQL Server コンシューマーが迅速にするためのインターフェイスを使用してデータを追加すると、既存[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。  
  
 セッションで SSPROP_ENABLEFASTLOAD を VARIANT_TRUE に設定した場合、その後にそのセッションから返される行セットのデータを読み取ることはできません。 SSPROP_ENABLEFASTLOAD が VARIANT_TRUE に設定されているときに型 IRowsetFastLoad のセッションで作成されるすべての行セットであります。 IRowsetFastLoad 行セットは行セットのフェッチ機能をサポートしていませんしたがって、これらの行セットからデータを読み取ることができません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|Description|  
|------------|-----------------|  
|[Irowsetfastload::commit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)|挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルに書き込みます。|  
|[Irowsetfastload::insertrow &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|一括コピー行セットに行を追加します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)   
 [データを一括コピー IRowsetFastLoad を使用した&#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [IROWSETFASTLOAD と ISEQUENTIALSTREAM (&) #40";"OLE DB"&"#41; を使用して SQL SERVER に BLOB データを送信します。](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
