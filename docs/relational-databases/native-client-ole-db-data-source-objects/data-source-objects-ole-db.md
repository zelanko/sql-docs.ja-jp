---
title: データ ソース オブジェクト (OLE DB) | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8bb984c789f759eb764ad580f971ab71c9fc946
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297690"
---
# <a name="data-source-objects-ole-db"></a>データ ソース オブジェクト (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントは、 などの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ストアへのリンクを確立するために使用される OLE DB インターフェイスのセットに対して、データ ソースという用語を使用します。 プロバイダーのデータ ソース オブジェクトのインスタンスを作成することは、ネイティブ クライアント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンシューマーの最初のタスクです。  
  
 すべての OLE DB プロバイダーは、そのプロバイダー自体のクラス ID (CLSID) を宣言します。 ネイティブ クライアント OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB プロバイダーの CLSID は、C/C++ GUID CLSID_SQLNCLI10です (シンボルSQLNCLI_CLSID参照する sqlncli.h ファイル内の適切な progid に解決されます)。 コンシューマーは、CLSID を指定して OLE **CoCreateInstance** 関数を使用し、データ ソース オブジェクトのインスタンスを作成します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントはインプロセス サーバーです。 ネイティブ クライアント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]OLE DB プロバイダー オブジェクトのインスタンスは、実行可能なコンテキストを示すためにCLSCTX_INPROC_SERVER マクロを使用して作成されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーのデータ ソース オブジェクトは、コンシューマーが既存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベースに接続できるようにする OLE DB 初期化インターフェイスを公開します。  
  
 ネイティブ クライアント OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB プロバイダを介して行われるすべての接続は、次のオプションを自動的に設定します。  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 この例では、クラス識別子マクロを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーのデータ ソース オブジェクトを作成し、**その IDBInitialize**インターフェイスへの参照を取得します。  
  
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
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーのデータ ソース オブジェクトのインスタンスが正常に作成されると、コンシューマー アプリケーションは、データ ソースを初期化し、セッションを作成して続行できます。 OLE DB セッションは、データへのアクセスや操作を可能にするインターフェイスを提供します。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダは、データ ソースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]初期化が正常に行なうため、 の指定されたインスタンスに最初に接続します。 いずれかのデータ ソース初期化インターフェイスで参照が保持されている間、または **IDBInitialize::Uninitialize** メソッドが呼び出されるまで、その最初の接続が維持されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースのプロパティ &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [データ ソース情報のプロパティ](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [初期化プロパティと承認プロパティ](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [セッション](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [セッション プロパティ - SQL Server Native Client OLE DB プロバイダー](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [保存されるデータ ソース オブジェクト](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
