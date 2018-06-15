---
title: SQL Server カーソルでデータの更新 |Microsoft ドキュメント
description: SQL Server カーソルでデータの更新
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
ms.openlocfilehash: 321700be33a81b511f30af7e7b263bd188e54264
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307711"
---
# <a name="updating-data-in-sql-server-cursors"></a>SQL Server カーソルでのデータ更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  フェッチとによるデータの更新時に[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソルの場合、OLE DB Driver for SQL Server コンシューマー アプリケーションが、同じ考慮事項およびその他のクライアント アプリケーションに適用される制約によってバインドされます。  
  
 同時実行データアクセス制御に関係するのは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソル内の行だけです。 コンシューマーから変更可能な行セットが要求されるときは、同時実行制御が DBPROP_LOCKMODE によって制御されます。 同時実行アクセス制御のレベルを変更するには、コンシューマーで行セットを開く前に DBPROP_LOCKMODE プロパティを設定します。  
  
 クライアント アプリケーションのデザインにより、トランザクションが長時間開かれたままの状態になる場合、トランザクション分離レベルが原因で行の位置指定が大幅に遅れる可能性があります。 既定では、SQL Server の OLE DB Driver は、DBPROPVAL_TI_READCOMMITTED によって指定された、read committed 分離レベルを使用します。 SQL Server の OLE DB Driver は、行セットの同時実行が読み取り専用の場合、ダーティ リード分離をサポートします。 そのため、コンシューマーは変更可能な行セットで、より高い分離レベルを要求できますが、より低い分離レベルは要求できません。  
  
## <a name="immediate-and-delayed-update-modes"></a>即時更新モードと遅延更新モード  
 即時更新モードでは、各呼び出しで**irowsetchange::setdata**へのラウンド トリップをにより、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 コンシューマーは、1 つの行に複数の変更を加えます場合、すべての変更を 1 つの送信をより効率的です**SetData**呼び出します。  
  
 遅延更新モードとのやり取りが行われた、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で示される行ごと、 *cRows*と*rghRows*のパラメーター **irowsetupdate::update**です。  
  
 どちらのモードでも、行セットに対してトランザクション オブジェクトが開いていないときは、1 つのラウンドトリップが個別のトランザクションを表します。  
  
 使用する場合は**irowsetupdate::update**、SQL Server の OLE DB Driver は示された各行を処理しようとしています。 無効なデータ、長さ、または状態値のいずれかの行のために発生するエラーでは、SQL Server の処理を OLE DB Driver は停止しません。 更新に関係する他のすべての行が変更されることも、そのような行がまったく変更されないこともあります。 コンシューマーは、返された調べる必要があります*prgRowStatus*配列時点を決定する任意の行のエラー、OLE DB Driver for SQL Server は DB_S_ERRORSOCCURRED を返します。  
  
 コンシューマーでは、特定の順序で行が処理されることを想定しないでください。 1 行以上の行に対してデータ変更を順序付けて処理することが必要な場合、アプリケーション ロジックで順序を確立し、トランザクションを開いてそのロジックをトランザクション内に含める必要があります。  
  
## <a name="see-also"></a>参照  
 [行セット内のデータの更新](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
