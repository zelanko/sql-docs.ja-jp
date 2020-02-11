---
title: データソースオブジェクト (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2683cdc7762f1f500918edce436153e0130d04bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73758259"
---
# <a name="data-source-objects-ole-db"></a>データ ソース オブジェクト (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client では、などのデータストアへのリンクを確立するために使用される一連の OLE DB インターフェイスに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]対して、データソースという用語を使用します。 プロバイダーのデータソースオブジェクトのインスタンスを作成することは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブクライアントコンシューマーの最初のタスクです。  
  
 すべての OLE DB プロバイダーは、そのプロバイダー自体のクラス ID (CLSID) を宣言します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの CLSID は、C/c + + GUID CLSID_SQLNCLI10 です (シンボル SQLNCLI_CLSID は、参照する SQLNCLI ファイルの正しい progid に解決されます)。 コンシューマーは、CLSID を指定して OLE **CoCreateInstance** 関数を使用し、データ ソース オブジェクトのインスタンスを作成します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は、インプロセスサーバーです。 Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB プロバイダーオブジェクトのインスタンスは、実行可能なコンテキストを示すために、CLSCTX_INPROC_SERVER マクロを使用して作成されます。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーのデータソースオブジェクトは、コンシューマーが既存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベースに接続できるようにする OLE DB 初期化インターフェイスを公開します。  
  
 Native Client OLE DB プロバイダーを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]介して行われるすべての接続では、次のオプションが自動的に設定されます。  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 この例では、クラス識別子マクロを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して、Native Client OLE DB プロバイダーのデータソースオブジェクトを作成し、 **IDBInitialize**インターフェイスへの参照を取得します。  
  
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
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのデータソースオブジェクトのインスタンスを正常に作成すると、データソースを初期化し、セッションを作成することによって、コンシューマーアプリケーションを続行できます。 OLE DB セッションは、データへのアクセスや操作を可能にするインターフェイスを提供します。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、データソースの初期化の一環と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して、の指定されたインスタンスへの最初の接続を行います。 いずれかのデータ ソース初期化インターフェイスで参照が保持されている間、または **IDBInitialize::Uninitialize** メソッドが呼び出されるまで、その最初の接続が維持されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データソースのプロパティ &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [データ ソース情報のプロパティ](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [初期化プロパティと承認プロパティ](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [セッション](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [セッション プロパティ - SQL Server Native Client OLE DB プロバイダー](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [保存されるデータ ソース オブジェクト](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
