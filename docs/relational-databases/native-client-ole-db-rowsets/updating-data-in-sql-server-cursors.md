---
title: SQL Server カーソルでデータの更新 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e64d5f5d4cb45d1e46156b14070dbfff181462ba
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430231"
---
# <a name="updating-data-in-sql-server-cursors"></a>SQL Server カーソルでのデータ更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  フェッチおよびを使用してデータを更新するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カーソルの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマー アプリケーションは、同じ考慮事項とその他の任意のクライアント アプリケーションに適用される制約によってバインドします。  
  
 同時実行データアクセス制御に関係するのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソル内の行だけです。 コンシューマーから変更可能な行セットが要求されるときは、同時実行制御が DBPROP_LOCKMODE によって制御されます。 同時実行アクセス制御のレベルを変更するには、コンシューマーで行セットを開く前に DBPROP_LOCKMODE プロパティを設定します。  
  
 クライアント アプリケーションのデザインにより、トランザクションが長時間開かれたままの状態になる場合、トランザクション分離レベルが原因で行の位置指定が大幅に遅れる可能性があります。 既定で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBPROPVAL_TI_READCOMMITTED によって指定される read committed 分離レベルを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、行セットの同時実行が読み取り専用である場合、ダーティ リード分離をサポートしています。 そのため、コンシューマーは変更可能な行セットで、より高い分離レベルを要求できますが、より低い分離レベルは要求できません。  
  
## <a name="immediate-and-delayed-update-modes"></a>即時更新モードと遅延更新モード  
 即時更新モードでは、各呼び出しで**irowsetchange::setdata**へのラウンド トリップの発生、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 コンシューマーが 1 つの行を複数の変更した場合は、1 つのすべての変更を送信する方が効率的**SetData**呼び出します。  
  
 遅延更新モードでラウンドト リップに加えられた、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で示される行ごと、 *cRows*と*rghRows*パラメーターの**irowsetupdate::update**します。  
  
 どちらのモードでも、行セットに対してトランザクション オブジェクトが開いていないときは、1 つのラウンドトリップが個別のトランザクションを表します。  
  
 使用する場合は**irowsetupdate::update**、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは指定された各行を処理しようとしています。 任意の行は停止しませんの無効なデータ、長さ、または状態の値が発生エラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによる処理します。 更新に関係する他のすべての行が変更されることも、そのような行がまったく変更されないこともあります。 コンシューマーは、返された調べる必要があります*prgRowStatus*配列は、特定のエラーを確認するときに行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DB_S_ERRORSOCCURRED を返します。  
  
 コンシューマーでは、特定の順序で行が処理されることを想定しないでください。 1 行以上の行に対してデータ変更を順序付けて処理することが必要な場合、アプリケーション ロジックで順序を確立し、トランザクションを開いてそのロジックをトランザクション内に含める必要があります。  
  
## <a name="see-also"></a>参照  
 [行セット内のデータの更新](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
