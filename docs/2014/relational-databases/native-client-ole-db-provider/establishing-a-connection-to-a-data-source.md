---
title: データ ソースへの接続の確立 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ed8a3011efa95df0ceed438341de9015d252d9d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056025"
---
# <a name="establishing-a-connection-to-a-data-source"></a>データ ソースへの接続の確立
  コンシューマーは、Native Client OLE DB プロバイダーにアクセスするために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] まず**CoCreateInstance**メソッドを呼び出すことによって、データソースオブジェクトのインスタンスを作成する必要があります。 一意のクラス ID (CLSID) で、各 OLE DB プロバイダーが識別されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの場合、クラス識別子は CLSID_SQLNCLI10 です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]参照する SQLNCLI に使用されている Native Client OLE DB プロバイダーに解決されるシンボル SQLNCLI_CLSID を使用することもできます。  
  
 データ ソース オブジェクトは、**IDBProperties** インターフェイスを公開します。コンシューマーは、このインターフェイスを使用して、サーバー名、データベース名、ユーザー ID、パスワードなどの基本的な認証情報を提供します。 **IDBProperties::SetProperties** メソッドが呼び出されて、これらのプロパティが設定されます。  
  
 同じコンピューター上で複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが実行されている場合、サーバー名を ServerName\InstanceName のように指定します。  
  
 データ ソース オブジェクトは、**IDBInitialize** インターフェイスも公開します。 プロパティを設定した後、**IDBInitialize::Initialize** メソッドを呼び出して、データ ソースへの接続を確立します。 次に例を示します。  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 この**CoCreateInstance**への呼び出しによって、CLSID_SQLNCLI10 (オブジェクトの作成に使用されるデータとコードに関連付けられた CSLID) に関連付けられたクラスの1つのオブジェクトが作成されます。 IID_IDBInitialize は、オブジェクトとの通信に使われるインターフェイス (**IDBInitialize**) の ID への参照です。  
  
 次に、データ ソースへの接続を初期化し、確立する関数の例を示します。  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client OLE DB プロバイダー アプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
