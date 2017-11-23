---
title: "データ ソース オブジェクト (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4f221f043fd976e5c0f6679e6f1dda29f5c199e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="data-source-objects-ole-db"></a>データ ソース オブジェクト (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client などのデータ ストアへのリンクを確立するために使用する OLE DB インターフェイスのセットの用語のデータ ソースを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 最初のタスクは、プロバイダーのデータ ソース オブジェクトのインスタンスを作成する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のコンシューマーです。  
  
 すべての OLE DB プロバイダーは、そのプロバイダー自体のクラス ID (CLSID) を宣言します。 CLSID、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、C/C++ GUID clsid_sqlncli10 です (シンボル SQLNCLI_CLSID は、適切に解決するには参照されている sqlncli.h ファイルに progid)。 CLSID を使用するコンシューマーは、OLE **CoCreateInstance**をデータ ソース オブジェクトのインスタンスを製造する関数。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は、インプロセス サーバーです。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダー オブジェクトは、実行可能なコンテキストを示すために、CLSCTX_INPROC_SERVER マクロを使用して作成されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのデータ ソース オブジェクトは、コンシューマーに既存の接続を許可する OLE DB 初期化インターフェイスを公開[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。  
  
 すべての接続を通じて行われますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが自動的にこれらのオプションを設定します。  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 この例では、クラス id マクロを使用して、作成、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのデータ ソース オブジェクトと参照を取得、 **IDBInitialize**インターフェイスです。  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
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
  
 インスタンスが正常に作成で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのデータ ソース オブジェクト、データ ソースを初期化し、セッションの作成で、コンシューマー アプリケーションを続行できます。 OLE DB セッションは、データへのアクセスや操作を可能にするインターフェイスを提供します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、最初の接続を指定のインスタンスに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]正常なデータ ソースの初期化の一部として。 まで、または任意のデータ ソース初期化インターフェイスでの参照が保持される限りは、接続を維持、 **:uninitialize**メソッドが呼び出されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースのプロパティ &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [データ ソース情報のプロパティ](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [初期化プロパティと承認プロパティ](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [セッション](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [セッション プロパティ - SQL Server Native Client OLE DB プロバイダー](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [保存されるデータ ソース オブジェクト](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
