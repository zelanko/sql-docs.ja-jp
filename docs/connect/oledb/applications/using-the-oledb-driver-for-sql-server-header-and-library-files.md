---
title: ドライバーを使用して、OLE DB SQL Server のヘッダーとライブラリ ファイルの |Microsoft ドキュメント
description: SQL Server のヘッダーとライブラリ ファイルの OLE DB Driver を使用します。
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f228442c31d754265769645a640b1eb1285c5897
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612147"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>SQL Server のヘッダーとライブラリ ファイルの OLE DB ドライバーを使用します。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server のヘッダーとライブラリ ファイルの OLE DB Driver は、インストール プロセス中に、OLE DB Driver for SQL Server SDK オプションが選択されているときにインストールされます。 アプリケーションを開発するときは、開発に必要なすべてのファイルを開発環境にコピーしてインストールすることが重要です。 インストールして、SQL Server の OLE DB Driver の再配布の詳細については、次を参照してください。[をインストールする OLE DB Driver for SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)です。  
  
 SQL Server のヘッダーとライブラリ ファイルの OLE DB Driver は、次の場所にインストールされます。  
  
 *%PROGRAM FILES%* \Microsoft SQL Server\Client SDK\OLEDB\180\SDK  
  
 カスタム アプリケーションにデータ アクセス機能を SQL Server の OLE DB ドライバーを追加する、OLE DB Driver for SQL Server ヘッダー ファイル (msoledbsql.h) を使用できます。 ヘッダー ファイルの SQL Server の OLE DB Driver には、すべての定義、属性、プロパティが含まれておりで導入された新機能を活用するために必要なインターフェイス[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。  
  
 だけでなく、OLE DB Driver for SQL Server のヘッダー ファイル、また、msoledbsql.lib ライブラリ ファイルには、エクスポート ライブラリでの[OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)機能します。  
  
 ヘッダー ファイルの SQL Server の OLE DB Driver は、Microsoft Data Access Components (MDAC) とを使用する sqloledb.h ヘッダー ファイルとの下位互換性ですがありません Clsid SQLOLEDB の (、OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] MDAC 付属) のシンボルまたは(これはサポートされていません、OLE DB Driver for SQL Server) の XML 機能します。    
  
 SQL Server の OLE DB Driver を使用する OLE DB アプリケーションは、のみ、msoledbsql.h を参照する必要があります。 アプリケーションは、SQL Server の MDAC (SQLOLEDB) と、OLE DB ドライバーの両方を使用する場合、sqloledb.h と msoledbsql.h の両方を参照することが、sqloledb.h への参照を先に指定する必要があります。  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>SQL Server のヘッダー ファイルの OLE DB ドライバーを使用します。  
 使用するには、OLE DB ドライバーの SQL Server のヘッダー ファイルの使用する必要があります、**含める**C/C++ プログラミング コード内のステートメント。 次のセクションでは、この OLE DB アプリケーションを実行する方法について説明します。  
  
> [!NOTE]  
>  または Visual Studio の C++ 2012 を使用してコンパイルした後で、OLE DB Driver for SQL Server のヘッダーとライブラリ ファイルはできるだけです。  
  
### <a name="ole-db"></a>OLE DB (OLE DB)  
 ドライバーを使用して、OLE DB プログラミング コードの次の行を使用して、OLE DB アプリケーションで SQL Server のヘッダー ファイルの。  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  アプリケーションがある場合、**を含める**、sqloledb.h 用のステートメント、**含める**msoledbsql.h のステートメントがその後に続く必要があります。  
  
 を SQL Server の OLE DB ドライバーによってデータ ソースへの接続を作成する場合は、プロバイダー名文字列として"MSOLEDBSQL"を使用します。  

  
## <a name="component-names-and-properties-by-version"></a>各バージョンのコンポーネント名とプロパティ  

|プロパティ|OLE DB Driver for SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|OLE DB ヘッダー ファイル名|msoledbsql.h|Sqloledb.h|  
|OLE DB プロバイダー DLL|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>静的リンクと BCP 関数  
 BCP 関数を使用するアプリケーションでは、アプリケーションのコンパイルに使用されたヘッダー ファイルおよびライブラリに付属するのと同じバージョンのドライバーを接続文字列で指定することが重要です。  
  
 詳細については、実行を参照してください。[一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md)です。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
