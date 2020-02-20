---
title: OLE DB Driver for SQL Server のヘッダーとライブラリ ファイルの使用 | Microsoft Docs
description: SQL Server ヘッダーとライブラリ ファイルでの OLE DB ドライバーの使用
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 93b906a0604772fe224b1e63eaf6eed9eb8af983
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989233"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>SQL Server ヘッダーとライブラリ ファイルでの OLE DB ドライバーの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server のヘッダー ファイルとライブラリ ファイルは、インストール プロセス中に [OLE DB Driver for SQL Server SDK] オプションを選択するとインストールされます。 アプリケーションを開発するときは、開発に必要なすべてのファイルを開発環境にコピーしてインストールすることが重要です。 OLE DB Driver for SQL Server のインストールと再配布の詳細については、「[OLE DB Driver for SQL Server のインストール](../../oledb/applications/installing-oledb-driver-for-sql-server.md)」を参照してください。  
  
 OLE DB Driver for SQL Server header のヘッダー ファイルとライブラリ ファイルは、次の場所にインストールされます。  
  
 *%PROGRAM FILES%* \Microsoft SQL Server\Client SDK\OLEDB\182\SDK  
  
 OLE DB Driver for SQL Server ヘッダー ファイル (msoledbsql.h) を使用して、OLE DB Driver for SQL Server データ アクセス機能をカスタム アプリケーションに追加できます。 OLE DB Driver for SQL Server ヘッダー ファイルには、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入された新しい機能を使用するために必要なすべての定義、属性、プロパティ、およびインターフェイスが含まれています。  
  
 OLE DB Driver for SQL Server ヘッダー ファイルに加えて、msoledbsql.lib ライブラリ ファイルもあります。これは [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) 機能のエクスポート ライブラリです。  
  
 OLE DB Driver for SQL Server ヘッダー ファイルは、MDAC (Microsoft Data Access Components) と共に使用する sqloledb.h ヘッダー ファイルに対して下位互換性がありますが、SQLOLEDB (MDAC 付属の OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) の CLSID や (OLE DB Driver for SQL Server でサポートされない) XML 機能のシンボルは含まれていません。    
  
 OLE DB Driver for SQL Server を使用する OLE DB アプリケーションで参照する必要があるのは、msoledbsql.h のみです。 1 つのアプリケーションで MDAC (SQLOLEDB) と OLE DB Driver for SQL Server の両方を使用する場合、sqloledb.h と msoledbsql.h の両方を参照できますが、sqloledb.h を先に参照する必要があります。  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>OLE DB Driver for SQL Server ヘッダー ファイルの使用  
 OLE DB Driver for SQL Server ヘッダー ファイルを使用するには、C/C++ プログラミング コードで **include** ステートメントを使用する必要があります。 以下のセクションでは、OLE DB アプリケーションでそれを行う方法について説明します。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server のヘッダー ファイルとライブラリ ファイルは、Visual Studio C++ 2012 以降を使用しないとコンパイルできません。  
  
### <a name="ole-db"></a>OLE DB (OLE DB)  
 OLE DB アプリケーションで OLE DB Driver for SQL Server ヘッダー ファイルを使用するには、次のプログラミング コードを使用します。  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  アプリケーションに sqloledb.h 用の **include** ステートメントがある場合は、その後に msoledbsql.h 用の **include** ステートメントを指定する必要があります。  
  
 OLE DB Driver for SQL Server によってデータ ソースに接続するときは、プロバイダー名文字列として "MSOLEDBSQL" を使用します。  

  
## <a name="component-names-and-properties-by-version"></a>各バージョンのコンポーネント名とプロパティ  

|プロパティ|OLE DB Driver for SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|OLE DB ヘッダー ファイル名|msoledbsql.h|Sqloledb.h|  
|OLE DB プロバイダー DLL|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>静的リンクと BCP 関数  
 BCP 関数を使用するアプリケーションでは、アプリケーションのコンパイルに使用されたヘッダー ファイルおよびライブラリに付属するのと同じバージョンのドライバーを接続文字列で指定することが重要です。  
  
 詳細については、「[一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
