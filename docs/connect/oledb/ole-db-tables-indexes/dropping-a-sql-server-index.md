---
title: SQL Server インデックスの削除 |Microsoft Docs
description: SQL Server の OLE DB ドライバーを使用して sql server インデックスの削除
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 990318037a3f1b35e311a983859507a364c52127
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669170"
---
# <a name="dropping-a-sql-server-index"></a>SQL Server インデックスの削除
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server を公開、 **iindexdefinition::dropindex**関数。 コンシューマーはこの関数を使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルからインデックスを削除できます。  
  
 複数の OLE DB Driver for SQL Server が公開されて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インデックスと主キーと UNIQUE 制約。 テーブル所有者、データベース所有者、一部の管理ロールのメンバーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルを変更して、制約を削除できます。 既定では、テーブル所有者だけが既存のインデックスを削除できます。 したがって、**DropIndex** が成功するか失敗するかは、アプリケーション ユーザーのアクセス権だけでなく、指定されたインデックスの種類によっても異なります。  
  
 コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
 インデックス名は、*pIndexID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。 *pIndexID* の *eKind* メンバーを DBKIND_NAME にする必要があります。 OLE DB Driver for SQL Server では、*pIndexID* が NULL の場合にテーブルのすべてのインデックスを削除する OLE DB 機能はサポートされません。 *pIndexID* が NULL の場合、E_INVALIDARG を返します。  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
