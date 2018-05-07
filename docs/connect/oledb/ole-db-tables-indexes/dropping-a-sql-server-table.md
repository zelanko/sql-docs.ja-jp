---
title: SQL Server テーブルを削除する |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して SQL Server テーブルを削除します。
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
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9b4c86501d6265a5a756d0d88ca6305cd96ee9d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dropping-a-sql-server-table"></a>SQL Server テーブルの削除
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server を公開、 **itabledefinition::droptable**関数を削除する、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベースからテーブル。  
  
 Unicode 文字の文字列として、テーブル名を指定、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* dbkind_name にする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
