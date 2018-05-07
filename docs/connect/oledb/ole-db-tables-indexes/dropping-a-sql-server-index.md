---
title: SQL Server インデックスの削除 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して sql server インデックスの削除
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
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6c1ce25341ac4d5f092e61f2d8f23d1ea0baaade
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dropping-a-sql-server-index"></a>SQL Server インデックスの削除

  OLE DB Driver for SQL Server を公開、 **iindexdefinition::dropindex**関数。 これにより、コンシューマーからのインデックスを削除する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。  
  
 SQL Server の OLE DB ドライバーが公開するいくつか[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インデックスと PRIMARY KEY 制約と UNIQUE 制約。 テーブルの所有者、データベース所有者、および管理者の役割の一部のメンバーを変更できる、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル、制約を削除します。 既定では、テーブル所有者だけが既存のインデックスを削除できます。 したがって、 **DropIndex**成功または失敗が示されているインデックスの種類にもアプリケーション ユーザーのアクセス権だけでなく依存します。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* dbkind_name にする必要があります。  
  
 コンシューマーは、Unicode 文字の文字列としてインデックスの名前を指定、 *pwszName*のメンバー、 *uName*共用体の*pIndexID*パラメーター。 *EKind*のメンバー *pIndexID* dbkind_name にする必要があります。 SQL Server の OLE DB Driver は、OLE DB の機能のすべてのインデックス、テーブルの削除をサポートしていませんとき*pIndexID*が null です。 場合*pIndexID*が null である E_INVALIDARG が返されます。  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
