---
title: データ ソース オブジェクト (OLE DB) |Microsoft ドキュメント
description: データ ソース オブジェクト (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], data source objects
- OLE DB Driver for SQL Server, data source objects
- MSOLEDBSQL, data source objects
- OLE DB Driver for SQL Server, data source objects
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- CLSID
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a69fbb260c594ad095872049b06b1f7084bfc29b
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665652"
---
# <a name="data-source-objects-ole-db"></a>データ ソース オブジェクト (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server などのデータ ストアへのリンクを確立するために使用する OLE DB インターフェイスのセットの用語のデータ ソースを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 OLE DB Driver for SQL Server コンシューマーの最初のタスクは、プロバイダーのデータ ソース オブジェクトのインスタンスを作成します。  
  
 すべての OLE DB プロバイダーは、そのプロバイダー自体のクラス ID (CLSID) を宣言します。 SQL Server の OLE DB ドライバーの CLSID が C/C++ GUID CLSID_MSOLEDBSQL (MSOLEDBSQL_CLSID が正しいを解決するシンボルを参照する msoledbsql.h ファイルに progid)。 CLSID を使用するコンシューマーは、OLE **CoCreateInstance**をデータ ソース オブジェクトのインスタンスを製造する関数。  
  
 OLE DB Driver for SQL Server は、インプロセス サーバーです。 SQL Server オブジェクトの OLE DB ドライバーのインスタンスは、実行可能なコンテキストを示すために、CLSCTX_INPROC_SERVER マクロを使用して作成されます。  
  
 OLE DB Driver for SQL Server データ ソース オブジェクトは、コンシューマーに既存の接続を許可する OLE DB 初期化インターフェイスを公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。  
  
 SQL Server の OLE DB ドライバーを通じて行うすべての接続では、これらのオプションが自動的に設定します。  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 この例は、SQL Server データ ソース オブジェクトと参照を取得するために、OLE DB ドライバーを作成する、クラス id マクロを使用してその**IDBInitialize**インターフェイスです。  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 OLE DB Driver for SQL Server データ ソース オブジェクトのインスタンスが正常に作成、データ ソースを初期化し、セッションを作成するコンシューマー アプリケーションを続行できます。 OLE DB セッションは、データへのアクセスや操作を可能にするインターフェイスを提供します。  
  
 SQL Server の OLE DB Driver は、最初の接続を指定のインスタンスに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]正常なデータ ソースの初期化の一部として。 まで、または任意のデータ ソース初期化インターフェイスでの参照が保持される限りは、接続を維持、 **:uninitialize**メソッドが呼び出されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースのプロパティ&#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [データ ソース情報のプロパティ](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [初期化プロパティと承認プロパティ](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [セッション](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [セッションのプロパティ - OLE DB Driver for SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [保存されるデータ ソース オブジェクト](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
