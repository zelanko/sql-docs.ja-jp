---
title: データ ソースへの接続を確立する |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用してデータ ソースへの接続を確立します。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB Driver for SQL Server]
- connections [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, data source connections
- CoCreateInstance method
- OLE DB data sources [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 7b4a864d10b109f32e552ed82d9d89868011496d
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666102"
---
# <a name="establishing-a-connection-to-a-data-source"></a>データ ソースへの接続の確立
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server にアクセスするコンシューマー必要があります最初のインスタンスを作成、データ ソース オブジェクトを呼び出して、 **CoCreateInstance**メソッドです。 一意のクラス ID (CLSID) で、各 OLE DB プロバイダーが識別されます。 OLE DB Driver for SQL Server、クラス識別子は CLSID_MSOLEDBSQL です。 参照されている msoledbsql.h で使用されている SQL Server の OLE DB ドライバーに解決される MSOLEDBSQL_CLSID シンボルを使用することもできます。  
  
 データ ソース オブジェクトの公開、 **IDBProperties**インターフェイスで、コンシューマーを使用してサーバー名、データベース名、ユーザー ID やパスワードなどの基本的な認証情報を提供します。 **Idbproperties::setproperties**をこれらのプロパティを設定するメソッドが呼び出されます。  
  
 同じコンピューター上で複数の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスが実行されている場合、サーバー名を ServerName\InstanceName のように指定します。  
  
 データ ソース オブジェクトに公開、 **IDBInitialize**インターフェイスです。 呼び出すことによって、データ ソースへの接続が確立されたプロパティを設定した後、 **idbinitialize::initialize**メソッドです。 以下に例を示します。  
  
```cpp
CoCreateInstance(CLSID_MSOLEDBSQL,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```
  
 この呼び出しを**CoCreateInstance** CLSID_MSOLEDBSQL (データとオブジェクトの作成に使用されるコードに関連付けられている CSLID) に関連付けられているクラスの 1 つのオブジェクトを作成します。 IID_IDBInitialize はインターフェイスの識別子への参照を (**IDBInitialize**) オブジェクトとの通信に使用します。  
  
 次の例では、初期化し、データ ソースへの接続を確立する方法を示します。
  
```cpp
#include "msoledbsql.h"
#include <stdio.h>

HRESULT InitializeAndEstablishConnection(IDBInitialize *&pIDBInitialize);

void main() {
    IDBInitialize       *pIDBInitialize = nullptr;
    HRESULT             hr = S_OK;

    // Initialize The Component Object Module Library
    CoInitialize(nullptr);

    hr = InitializeAndEstablishConnection(pIDBInitialize);
    if (FAILED(hr)) {
        printf("Failed to establish connection.\r\n");
        goto _ExitMain;
    }

    // Insert code that uses the established connection

_ExitMain:
    // Free Up All Allocated Memory
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
        pIDBInitialize = nullptr;
    }

    // Release The Component Object Module Library
    CoUninitialize();
}

HRESULT InitializeAndEstablishConnection(IDBInitialize *&pIDBInitialize) {
    IDBProperties   *pIDBProperties = nullptr;
    DBPROP          InitProperties[3] = { 0 };
    DBPROPSET       rgInitPropSet[1] = { 0 };
    HRESULT         hr = S_OK;

    // Obtain access to the OLE DB Driver for SQL Server.  
    hr = CoCreateInstance(CLSID_MSOLEDBSQL,
                          NULL,
                          CLSCTX_INPROC_SERVER,
                          IID_IDBInitialize,
                          (void **)&pIDBInitialize);
    if (FAILED(hr)) {
        printf("Failed to obtain access to the OLE DB Driver.\r\n");
        goto _ExitInitialize;
    }
    // Initialize property values needed to establish connection.  
    for (int i = 0; i < 3; i++) {
        VariantInit(&InitProperties[i].vValue);
    }

    // Server name.  
    // See DBPROP structure for more information on InitProperties  
    InitProperties[0].dwPropertyID = DBPROP_INIT_DATASOURCE;
    InitProperties[0].vValue.vt = VT_BSTR;
    InitProperties[0].vValue.bstrVal = SysAllocString(L"Server");
    InitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;
    InitProperties[0].colid = DB_NULLID;

    // Database.  
    InitProperties[1].dwPropertyID = DBPROP_INIT_CATALOG;
    InitProperties[1].vValue.vt = VT_BSTR;
    InitProperties[1].vValue.bstrVal = SysAllocString(L"database");
    InitProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;
    InitProperties[1].colid = DB_NULLID;

    // Username (login).  
    InitProperties[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;
    InitProperties[2].vValue.vt = VT_BSTR;
    InitProperties[2].vValue.bstrVal = SysAllocString(L"SSPI");
    InitProperties[2].dwOptions = DBPROPOPTIONS_REQUIRED;
    InitProperties[2].colid = DB_NULLID;

    // Construct the DBPROPSET structure(rgInitPropSet). The   
    // DBPROPSET structure is used to pass an array of DBPROP   
    // structures (InitProperties) to the SetProperties method.  
    rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;
    rgInitPropSet[0].cProperties = 3;
    rgInitPropSet[0].rgProperties = InitProperties;

    // Set initialization properties.  
    hr = pIDBInitialize->QueryInterface(IID_IDBProperties,
                                        (void **)&pIDBProperties);
    if (FAILED(hr)) {
        printf("Failed to obtain an IDBProperties interface.\r\n");
        goto _ExitInitialize;
    }
    hr = pIDBProperties->SetProperties(1, rgInitPropSet);
    if (FAILED(hr)) {
        printf("Failed to set initialization properties.\r\n");
        goto _ExitInitialize;
    }

    // Now establish the connection to the data source.  
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr)) {
        printf("Failed to establish connection with the server.\r\n");
        goto _ExitInitialize;
    }

_ExitInitialize:
    if (pIDBProperties)
    {
        pIDBProperties->Release();
        pIDBProperties = nullptr;
    }

    if (FAILED(hr))
    {
        if (pIDBInitialize)
        {
            pIDBInitialize->Release();
            pIDBInitialize = nullptr;
        }
    }

    return hr;
}
```  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のアプリケーションの作成](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
