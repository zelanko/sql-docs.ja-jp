---
title: SQL Server テーブルに列を追加する |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して SQL Server テーブルに列を追加します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- OLE DB Driver for SQL Server, columns
- adding columns
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 2f49f014e29401d0f99bd5f9bd59551c94255399
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-column-to-a-sql-server-table"></a>SQL Server テーブルへの列の追加
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server を公開、 **itabledefinition::addcolumn**関数。 これにより、列を追加するコンシューマー、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。  
  
 列を追加すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブルは、OLE DB Driver は SQL Server コンシューマーを次のように制限します。  
  
-   DBPROP_COL_AUTOINCREMENT が VARIANT_TRUE の場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   使用して、列が定義されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **タイムスタンプ**データ型、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   それ以外の列定義の場合、DBPROP_COL_NULLABLE は VARIANT_TRUE にする必要があります。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* dbkind_name にする必要があります。  
  
 Unicode 文字の文字列として、新しい列名が指定されて、 *pwszName*のメンバー、 *uName*共用体の*dbcid* DBCOLUMNDESC パラメーターのメンバー*pColumnDesc*です。 *EKind*メンバーは dbkind_name にする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)  
  
  
