---
title: BLOB と OLE オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d0cb9751940489513f939ab8ee52728c6b75e925
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297693"
---
# <a name="blobs-and-ole-objects"></a>BLOB と OLE オブジェクト
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、バイナリ ラージ オブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](BLOB) として **、ntext**、 **text**、 **image**、 **varchar(max)** **、nvarchar(max)** **、varbinary(max)**、および xml データ型へのコンシューマー アクセスをサポートする**ISequentialStream**インターフェイスを公開します。 **ISequentialStream** の **Read** メソッドを使用すると、扱いやすい単位で大量のデータを取得できます。  
  
 この機能を示すサンプルについては、「[大きなデータの設定 (OLE DB)](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md)」を参照してください。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、コンシューマーがデータ変更にバインドされたアクセサーにインターフェイス ポインターを提供するときに、コンシューマー実装**の IStorage**インターフェイスを使用できます。  
  
 大きな値の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の場合、ネイティブ クライアント OLE DB プロバイダーは **、IRowset**および DDL インターフェイスで型サイズの前提をチェックします。 最大サイズが無制限に設定された**varchar**型 **、nvarchar**型、**および varbinary**型の列は、スキーマ行セットと列データ型を返すインターフェイスを通じて ISLONG として表されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダは、それぞれ DBTYPE_STR、DBTYPE_BYTES、およびDBTYPE_WSTRとして**varchar(max)** 型 **、varbinary(max)** 型、**および nvarchar(max)** 型を公開します。  
  
 これらの型を使用するには、アプリケーションには次のオプションがあります。  
  
-   データ型 DBTYPE_STR、DBTYPE_BYTES、または DBTYPE_WSTR としてバインドします。 バッファーのサイズが十分でない場合、これらのデータ型は以前のリリースでの動作と同様に (以前よりも大きな値を格納できるようになりましたが)、切り捨てが行われます。  
  
-   データ型としてバインドし、DBTYPE_BYREF も指定します。  
  
-   DBTYPE_IUNKNOWN としてバインドし、ストリーミングを使用します。  
  
 DBTYPE_IUNKNOWN にバインドすると、ISequentialStream ストリーム機能が使用されます。 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、ストアド プロシージャがクライアントにDBTYPE_IUNKNOWNとして公開される戻り値としてこれらのデータ型を返すシナリオを容易にするために、大きな値のデータ型のDBTYPE_IUNKNOWNとして、バインディング出力パラメーターをサポートします。  
  
## <a name="storage-object-limitations"></a>ストレージ オブジェクトの制限事項  
  
-   ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、1 つのオープン ストレージ オブジェクトのみをサポートできます。 複数の **ISequentialStream** インターフェイス ポインターへの参照を取得するために、複数のストレージ オブジェクトを開こうとすると、DBSTATUS_E_CANTCREATE が返されます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーでは、DBPROP_BLOCKINGSTORAGEOBJECTS読み取り専用プロパティの既定値はVARIANT_TRUE。 この値は、ストレージ オブジェクトがアクティブである場合に、(ストレージ オブジェクト以外の) 一部のメソッドが失敗して E_UNEXPECTED が返されることを示します。  
  
-   コンシューマーが実装するストレージ オブジェクトによって提供されるデータの長さは、ストレージ オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]参照する行アクセサーが作成されるときに、ネイティブ クライアント OLE DB プロバイダに認識される必要があります。 コンシューマー側では、アクセサーの作成に使用する DBBINDING 構造体に長さのインジケーターをバインドする必要があります。  
  
-   行に複数の大きなデータ値が含まれ、DBPROP_ACCESSORDERがDBPROPVAL_AO_RANDOMされていない場合、コンシューマーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ネイティブ クライアント OLE DB プロバイダーカーソルサポートの行セットを使用して行データを取得するか、大きなデータ値をすべて処理してから他の行の値を取得する必要があります。 DBPROP_ACCESSORDERがDBPROPVAL_AO_RANDOM場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーは、すべての xml データ型をバイナリ ラージ オブジェクト (BLOB) としてキャッシュし、任意の順序でアクセスできるようにします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [大きなデータの取得](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [大きなデータの設定](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [BLOB 出力パラメーターのストリーミング サポート](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB&#41;&#40;SQL Server ネイティブ クライアント](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [大きな値をとるデータ型の使用](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
