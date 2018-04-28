---
title: SQL Server の OLE DB Driver のシステム要件 |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーの要件
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c465001d1e09ac229b0dc8cfd16124df3143e3d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB Driver のシステム要件
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ アクセス機能 (MARS など) を使用するには、次のソフトウェアがインストールされている必要があります。  

-   OLE DB Driver for SQL Server は、クライアントです。  

-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス (サーバー)   

> [!NOTE]  
>  このソフトウェアは、必ず管理者特権でログオンしてからインストールしてください。  

## <a name="operating-system-requirements"></a>必要なオペレーティング システム  
 SQL Server の OLE DB ドライバーをサポートするオペレーティング システムの一覧は、次を参照してください。 [OLE DB driver for SQL Server サポート ポリシー](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md)です。  

## <a name="sql-server-requirements"></a>SQL Server の要件  
 SQL Server のデータにアクセスする OLE DB Driver を使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベースのインスタンスが存在する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールします。  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SQL Server のすべてのバージョンの MDAC、Windows Data Access Components、および OLE DB ドライバーのすべてのバージョンからの接続をサポートします。 古いクライアント バージョンで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合、クライアントで認識されないサーバーのデータ型は、クライアント バージョンと互換する型にマップされます。 詳細については、このトピックの「クライアント バージョンのデータ型の互換性」をご覧ください。  

## <a name="cross-language-requirements"></a>言語間の要件  
 OLE DB Driver for SQL Server の英語版がサポートされるオペレーティング システムのすべてのローカライズ版でサポートされています。 ローカライズされた OLE DB Driver for SQL Server のバージョンと同じ言語であるローカライズされたオペレーティング システムでは、OLE DB Driver for SQL Server のローカライズされたバージョンがサポートされています。 OLE DB Driver for SQL Server のローカライズ版は、対応する言語設定がインストールされている限りでサポートされるオペレーティング システムの英語版でもサポートされます。  

 アップグレードの要件を次に示します。  

-   OLE DB Driver for SQL Server の英語版は、SQL Server の OLE DB ドライバーのすべてのローカライズ版にアップグレードできます。  

-   OLE DB Driver for SQL Server のローカライズ版は、同じ言語の SQL Server の OLE DB Driver のローカライズ版にアップグレードできます。  

-   OLE DB Driver for SQL Server のローカライズ版は、SQL Server の OLE DB Driver の英語版にアップグレードできます。  

-   OLE DB Driver for SQL Server のローカライズ版は、ローカライズされた OLE DB Driver for SQL Server のバージョンを別のローカライズされた言語にアップグレードすることはできません。  

## <a name="data-type-compatibility-for-client-versions"></a>クライアント バージョンのデータ型の互換性  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Driver for SQL Server マップ新しいデータ型を古いデータ型と互換性がある下位クライアントでは、次の表に示すようにします。  

 OLE DB と ADO アプリケーションを使用して、 **DataTypeCompatibility** OLE DB ドライバーと古いデータ型で動作する SQL Server の接続文字列キーワードです。 ときに**DataTypeCompatibility = 80**、OLE DB クライアントの接続を使用して、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]表形式データ ストリーム (TDS) バージョンには、TDS バージョンではなくです。 つまり、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降のデータ型、ダウン レベルの変換が実行されます OLE DB Driver ではなく、サーバーで SQL Server 用です。 またこの場合は、接続で使用可能な機能が、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 機能セットに制限されます。 新しいデータ型または機能を使用しようとすると、API 呼び出し時にすぐに検出されます。無効な要求はサーバーに渡されず、呼び出し元のアプリケーションにエラーが返されます。   


 IDBInfo::GetKeywords は常には影響しません、接続のサーバー バージョンに対応するキーワードの一覧を返します**DataTypeCompatibility**です。  

|データ型|SQL Server Native Client<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|OLE DB Driver for SQL Server|Windows Data Access Components、MDAC、<br /><br /> OLE DB Driver for SQL Server の OLE DB アプリケーション datatypecompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<8 Kb 以下)|udt|Udt|Udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|テキスト|  
|nvarchar(max)|nvarchar|nvarchar|nvarchar|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (8 KB を超える)|udt|varbinary|varbinary|image|  
|date|date|varchar|varchar|Varchar|  
|datetime2|datetime2|varchar|varchar|Varchar|  
|datetimeoffset|datetimeoffset|varchar|varchar|Varchar|  
|time|time|varchar|varchar|Varchar|  

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [OLE DB Driver for SQL Server のインストール](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
