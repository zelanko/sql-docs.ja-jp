---
title: FILESTREAM のサポート |Microsoft ドキュメント
description: OLE DB driver for SQL Server の FILESTREAM のサポート
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb5c5abb611223d31af9832c512a418b18ac78a9
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="filestream-support"></a>FILESTREAM のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

FILESTREAM を使用すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を経由するか、Windows ファイル システムに直接アクセスすることで、大きなバイナリ値の格納やアクセスが可能になります。 大きなバイナリ値とは、2 ギガバイト (GB) よりも大きい値です。 強化された FILESTREAM のサポートの詳細については、次を参照してください。 [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md)です。  
  
データベース接続が開かれたときに**@@TEXTSIZE**  (「無制限」)、既定では-1 に設定します。  
  
Windows ファイル システムの API を使用して、FILESTREAM 列にアクセスし、更新することもできます。  
  
詳細については、次の各トピックを参照してください。  
  
-   [FILESTREAM のサポート&#40;OLE DB&#41;](../../oledb/ole-db/filestream-support-ole-db.md)    
  
-   [OpenSqlFilestream による FILESTREAM データへのアクセス](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>FILESTREAM 列のクエリ  
OLE DB のスキーマ行セットでは、列が FILESTREAM 列かどうかは報告されません。 ITableDefinition OLE DB では、FILESTREAM 列を作成するのには使用できません。    
  
FILESTREAM 列を作成する、または FILESTREAM 列として使用する既存の列を検出するために使用できます、 **is_filestream**の列、 [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)カタログ ビューです。  
  
以下に例を示します。  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>下位互換性  
SQL Server の OLE DB Driver を使用してコンパイルしたクライアントとアプリケーションが接続する場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)])、し**varbinary (max)**動作を動作と互換性があります導入された[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client に[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 返されるデータの最大サイズが 2 GB に制限されます。 大きな結果値が 2 GB の切り捨てが発生して、「文字列データ右側が切り捨てられました」警告が返されます。 
  
データ型の互換性が 80 に設定されている場合は、クライアントの動作で下位クライアントとの互換性が維持されます。  
  
SQLOLEDB または以前にリリースされたその他のプロバイダーを使用するクライアントに対して、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、 **varbinary (max)**はマップをイメージにします。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
