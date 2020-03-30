---
title: 行セット内のデータの更新 | Microsoft Docs
description: OLE DB Driver for SQL Server を使用した行セット内のデータの更新
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e19128d6defa2c154cc8bddbcc4bcaa761b58a2b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015339"
---
# <a name="updating-data-in-rowsets"></a>行セット内のデータの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server 用の OLE DB ドライバーでは、コンシューマーが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータを含む変更可能な行セットを更新するときに、該当するデータが更新されます。 コンシューマーが **IRowsetChange** インターフェイスまたは **IRowsetUpdate** インターフェイスのいずれかのサポートを要求すると、変更可能な行セットが作成されます。  
  
 OLE DB Driver for SQL Server による変更が可能な行セットはすべて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソルを使用して、行セットがサポートされます。 行セット プロパティ DBPROP_LOCKMODE は、カーソルでの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のコンカレンシー制御動作を変更し、更新可能な行セット内の行をフェッチする動作や、その行セット内のデータの整合性に関するエラーを生成する動作を決定します。  
  
 OLE DB Driver for SQL Server では、更新前と更新後の行の同期がサポートされます。  
  
> [!NOTE]  
>  IRowChange::SetColumns を使用して、行オブジェクトの 1 つ以上の名前付き列の値を設定できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server カーソルでのデータ更新](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [行の再同期](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
