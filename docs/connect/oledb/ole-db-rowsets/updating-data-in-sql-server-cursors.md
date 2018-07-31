---
title: SQL Server カーソルでデータの更新 |Microsoft Docs
description: SQL Server カーソルでのデータ更新
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b9351b2fd5000e2d93ed2c66446a16b8dc718c0c
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107714"
---
# <a name="updating-data-in-sql-server-cursors"></a>SQL Server カーソルでのデータ更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソルによってデータをフェッチおよび更新する場合、OLE DB Driver for SQL Server のコンシューマー アプリケーションについても、他のクライアント アプリケーションと同様の考慮事項や制約があてはまります。  
  
 同時実行データアクセス制御に関係するのは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソル内の行だけです。 コンシューマーから変更可能な行セットが要求されるときは、同時実行制御が DBPROP_LOCKMODE によって制御されます。 同時実行アクセス制御のレベルを変更するには、コンシューマーで行セットを開く前に DBPROP_LOCKMODE プロパティを設定します。  
  
 クライアント アプリケーションのデザインにより、トランザクションが長時間開かれたままの状態になる場合、トランザクション分離レベルが原因で行の位置指定が大幅に遅れる可能性があります。 既定では、OLE DB Driver for SQL Server は、DBPROPVAL_TI_READCOMMITTED によって指定される READ COMMITTED 分離レベルを使用します。 OLE DB Driver for SQL Server は、行セットの同時実行は読み取り専用である場合に、ダーティ リード分離をサポートします。 そのため、コンシューマーは変更可能な行セットで、より高い分離レベルを要求できますが、より低い分離レベルは要求できません。  
  
## <a name="immediate-and-delayed-update-modes"></a>即時更新モードと遅延更新モード  
 即時更新モードでは、**IRowsetChange::SetData** を呼び出すたびに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との間にラウンドトリップが発生します。 コンシューマーが 1 つの行に複数の変更を加える場合は、**SetData** を 1 回呼び出してすべての変更を実行する方が効率が高くなります。  
  
 遅延更新モードでは、**IRowsetUpdate::Update** の *cRows* パラメーターと *rghRows* パラメーターに示される行ごとに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との間にラウンドトリップが発生します。  
  
 どちらのモードでも、行セットに対してトランザクション オブジェクトが開いていないときは、1 つのラウンドトリップが個別のトランザクションを表します。  
  
 使用する場合は**irowsetupdate::update**、OLE DB Driver for SQL Server は指定された各行を処理しようとしています。 任意の行の無効なデータ、長さ、または状態値が原因でエラーが発生しても、OLE DB Driver for SQL Server による処理は停止されません。 更新に関係する他のすべての行が変更されることも、そのような行がまったく変更されないこともあります。 OLE DB Driver for SQL Server から DB_S_ERRORSOCCURRED が返されたときは、コンシューマーでは返された *prgRowStatus* 配列を調べて、特定の行で発生したエラーを判断する必要があります。  
  
 コンシューマーでは、特定の順序で行が処理されることを想定しないでください。 1 行以上の行に対してデータ変更を順序付けて処理することが必要な場合、アプリケーション ロジックで順序を確立し、トランザクションを開いてそのロジックをトランザクション内に含める必要があります。  
  
## <a name="see-also"></a>参照  
 [行セット内のデータの更新](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
