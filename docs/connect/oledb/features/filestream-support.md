---
title: FILESTREAM のサポート |Microsoft Docs
description: OLE DB Driver for SQL Server の FILESTREAM のサポート
ms.custom: ''
ms.date: 09/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a548cfda44d40ba7ac37aaf4465c589c7256ffe7
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978056"
---
# <a name="filestream-support"></a>FILESTREAM のサポート
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]以降、SQL Server 用の OLE DB ドライバーでは、拡張された FILESTREAM 機能がサポートされています。 サンプルについては、「 [Filestream と OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md)」を参照してください。  

FILESTREAM を使用すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を経由するか、Windows ファイル システムに直接アクセスすることで、大きなバイナリ値の格納やアクセスが可能になります。 大きなバイナリ値とは、2 ギガバイト (GB) よりも大きい値です。 拡張された FILESTREAM サポートの詳細については、「 [filestream &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md)」を参照してください。  
  
データベース接続を開くと、 **@@TEXTSIZE** が既定で -1 (無制限) に設定されます。  
  
Windows ファイル システムの API を使用して、FILESTREAM 列にアクセスし、更新することもできます。  
  
詳細については、「[OpenSqlFilestream による FILESTREAM データへのアクセス](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)」を参照してください。  
  
## <a name="querying-for-filestream-columns"></a>FILESTREAM 列のクエリ  
OLE DB のスキーマ行セットでは、列が FILESTREAM 列かどうかは報告されません。 また、OLE DB の ITableDefinition を使用して FILESTREAM 列を作成することはできません。    
  
FILESTREAM 列を作成する場合や、既存の FILESTREAM 列を検出する場合は、[sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) カタログ ビューの **is_filestream** 列を使用できます。  
  
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
クライアントが SQL Server 用の OLE DB ドライバーを使用してコンパイルされ、アプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]が[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ( [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を通じて) に接続している場合、 **varbinary (max)** 動作[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]はによって導入された動作と互換性があります。の[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]Native Client。 返されるデータの最大サイズが 2 GB に制限されます。 戻り値が 2 GB より大きい場合は切り捨てが行われ、"文字列データの右側が切り捨てられました" という警告が返されます。 
  
データ型の互換性が 80 に設定されている場合は、クライアントの動作で下位クライアントとの互換性が維持されます。  
  
[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前にリリースされた SQLOLEDB などのプロバイダーを使用しているクライアントでは、**varbinary(max)** が image にマップされます。  
  
## <a name="comments"></a>コメント
- 2 GB を超える**varbinary (max)** 値を送受信するために、アプリケーションではパラメーターと結果のバインドで**DBTYPE_IUNKNOWN**を使用します。 パラメーターの場合、プロバイダーは ISequentialStream の IUnknown:: QueryInterface と ISequentialStream を返す結果を呼び出す必要があります。  

-  OLE DB の場合、ISequentialStream 値に関連するチェックは緩和されます。 *Wtype*が**DBBINDING**構造体で**DBTYPE_IUNKNOWN**の場合、 *dwpart*から**DBPART_LENGTH**を省略するか、データの長さ (オフセット*oblength* ) を設定して、長さのチェックを無効にすることができます。バッファー) ~ 0 までです。 この場合、プロバイダーは値の長さをチェックせず、ストリームで利用可能なすべてのデータを要求し、返します。 この変更は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (以降の) サーバーに接続する場合に限り、すべてのラージ オブジェクト (LOB) 型と XML に適用されます。 これにより、既存のアプリケーションや下位レベルのサーバーとの一貫性や下位互換性を維持しつつ、より柔軟な開発が可能になります。  この変更は、データを転送するすべてのインターフェイス (主に IRowset:: GetData、ICommand:: Execute、および IRowsetFastLoad:: InsertRow) に影響します。
 

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
