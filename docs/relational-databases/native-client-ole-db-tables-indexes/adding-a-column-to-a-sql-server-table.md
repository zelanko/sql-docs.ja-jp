---
title: SQL Server テーブルに列の追加 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49f73e958f10b122047cfc551b8de3cfb5322be6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069599"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>SQL Server テーブルへの列の追加
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **itabledefinition::addcolumn**関数。 これにより、コンシューマーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに列を追加できます。  
  
 列を追加すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、テーブル、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーは次の制約します。  
  
-   DBPROP_COL_AUTOINCREMENT が VARIANT_TRUE の場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **timestamp** データ型を使用して列を定義している場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   それ以外の列定義の場合、DBPROP_COL_NULLABLE は VARIANT_TRUE にする必要があります。  
  
 コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
 新しい列名は、DBCOLUMNDESC パラメーター *pColumnDesc* の *dbcid* メンバー内にある、*uName* 共用体の *pwszName* メンバーに Unicode 文字列として指定されます。 *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [テーブルとインデックス](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
