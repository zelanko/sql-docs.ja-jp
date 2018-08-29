---
title: SQL Server テーブルの削除 |Microsoft Docs
description: SQL Server の OLE DB ドライバーを使用して SQL Server テーブルの削除
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 24dac40a7587db9c6b603377ddbf5ffd8e03506c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028888"
---
# <a name="dropping-a-sql-server-table"></a>SQL Server テーブルの削除
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server を公開、 **itabledefinition::droptable**関数を削除する、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベースからテーブル。  
  
 テーブル名は、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
