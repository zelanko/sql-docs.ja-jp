---
title: FILESTREAM のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3eb1f9c51f6d21ea0684c33df33817003564d7d7
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703123"
---
# <a name="filestream-support"></a>FILESTREAM のサポート
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  FILESTREAM を使用すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を経由するか、Windows ファイル システムに直接アクセスすることで、大きなバイナリ値の格納やアクセスが可能になります。 大きなバイナリ値とは、2 ギガバイト (GB) よりも大きい値です。 強化された FILESTREAM のサポートの詳細については、次を参照してください。 [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md)です。  
  
 データベース接続が開かれたときに **@@TEXTSIZE**  (「無制限」)、既定では-1 に設定します。  
  
 Windows ファイル システムの API を使用して、FILESTREAM 列にアクセスし、更新することもできます。  
  
 詳細については、次の各トピックを参照してください。  
  
-   [FILESTREAM のサポート&#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [FILESTREAM のサポート&#40;ODBC&#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [OpenSqlFilestream による FILESTREAM データへのアクセス](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>FILESTREAM 列のクエリ  
 OLE DB のスキーマ行セットでは、列が FILESTREAM 列かどうかは報告されません。 ITableDefinition OLE DB では、FILESTREAM 列を作成するのには使用できません。  
  
 ODBC の SQLColumns などのカタログ関数では、列は、FILESTREAM 列かどうかは報告されません。  
  
 FILESTREAM 列を作成する、または FILESTREAM 列として使用する既存の列を検出するために使用できます、 **is_filestream**の列、 [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)カタログ ビューです。  
  
 以下に例を示します。  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>下位互換性  
 バージョンを使用してコンパイルしたクライアント場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client に含まれている[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、アプリケーションが接続して[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、 **varbinary (max)** と互換性のある動作[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. 返されるデータの最大サイズが 2 GB に制限されます。 大きな結果値が 2 GB の切り捨てが発生して、「文字列データ右側が切り捨てられました」警告が返されます。  
  
 データ型の互換性が 80 に設定されている場合は、クライアントの動作で下位クライアントとの互換性が維持されます。  
  
 SQLOLEDB または以前にリリースされたその他のプロバイダーを使用するクライアント用、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]バージョンの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、 **varbinary (max)** はマップをイメージにします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
