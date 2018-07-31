---
title: OLE DB Driver for SQL Server のシステム要件 | Microsoft Docs
description: OLE DB Driver for SQL Server の要件
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: d7b390f385f94dbe65d667440d27e748a84bcb86
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106578"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のシステム要件
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ アクセス機能 (MARS など) を使用するには、次のソフトウェアがインストールされている必要があります。  

-   OLE DB Driver for SQL Server クライアントをします。  

-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス (サーバー)   

> [!NOTE]  
>  このソフトウェアは、必ず管理者特権でログオンしてからインストールしてください。  

## <a name="operating-system-requirements"></a>必要なオペレーティング システム  
 OLE DB Driver for SQL Server をサポートしているオペレーティング システムの一覧では、次を参照してください。 [OLE DB driver for SQL Server のサポート ポリシー](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md)します。  

## <a name="sql-server-requirements"></a>SQL Server の要件  
 SQL Server のデータにアクセスする OLE DB ドライバーを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベースのインスタンスがある必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールします。  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] は、MDAC、Windows Data Access Components、および OLE DB Driver for SQL Server のすべてのバージョンからの接続をサポートします。 古いクライアント バージョンで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合、クライアントで認識されないサーバーのデータ型は、クライアント バージョンと互換する型にマップされます。 詳細については、このトピックの「クライアント バージョンのデータ型の互換性」をご覧ください。  

## <a name="cross-language-requirements"></a>言語間の要件  
 OLE DB Driver for SQL Server の英語版は、サポートされるオペレーティング システムのすべてのローカライズされたバージョンでサポートされます。 OLE DB Driver for SQL Server のローカライズ版は、ローカライズされた OLE DB Driver for SQL Server のバージョンと同じ言語であるローカライズされたオペレーティング システムでサポートされます。 また、対応する言語設定がインストールされていれば、サポートされているオペレーティング システムの英語版でも利用できます。  

 アップグレードの要件を次に示します。  

-   OLE DB Driver for SQL Server の英語版は、SQL Server の OLE DB ドライバーのすべてのローカライズ版にアップグレードできます。  

-   OLE DB Driver for SQL Server のローカライズ版は、同じ言語の SQL Server の OLE DB ドライバーのローカライズ版にアップグレードできます。  

-   OLE DB Driver for SQL Server のローカライズ版は、SQL Server の OLE DB ドライバーの英語版にアップグレードできます。  

-   OLE DB Driver for SQL Server のローカライズ版は、ローカライズされた OLE DB Driver for SQL Server のバージョンの別のローカライズされた言語にアップグレードできません。  

## <a name="data-type-compatibility-for-client-versions"></a>クライアント バージョンのデータ型の互換性  
 以下の表に示すように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および OLE DB Driver for SQL Server は新しいデータ型を、下位クライアントと互換する古いデータ型にマップします。  

 OLE DB と ADO アプリケーションで使用できます、 **DataTypeCompatibility** OLE DB Driver for SQL Server を古いデータ型で動作すると、接続文字列キーワードです。 **DataTypeCompatibility=80** の場合、OLE DB クライアントは TDS (表形式データ ストリーム) バージョンではなく、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] TDS バージョンを使用して接続します。 つまり、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のデータ型の場合、OLE DB Driver for SQL Server ではなく、サーバーによって下位変換が実行されます。 またこの場合は、接続で使用可能な機能が、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 機能セットに制限されます。 新しいデータ型または機能を使用しようとすると、API 呼び出し時にすぐに検出されます。無効な要求はサーバーに渡されず、呼び出し元のアプリケーションにエラーが返されます。   


 IDBInfo::GetKeywords は常には影響されません、接続のサーバー バージョンに対応するキーワードの一覧を返します**DataTypeCompatibility**します。  

|データ型|SQL Server Native Client<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|OLE DB Driver for SQL Server|Windows Data Access Components、MDAC、<br /><br /> OLE DB Driver for SQL Server OLE DB アプリケーションでは、DataTypeCompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8Kb)|udt|udt|udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|Text|  
|nvarchar(max)|NVARCHAR|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (8 KB を超える)|varbinary|udt|udt|image|  
|日付|varchar|日付|日付|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [OLE DB Driver for SQL Server のインストール](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
