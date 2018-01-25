---
title: "Blob と OLE オブジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-blobs
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
caps.latest.revision: "43"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 03eb28507a7fa0fdc2bf8df55dbb39356f24109c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="blobs-and-ole-objects"></a>BLOB と OLE オブジェクト
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **ISequentialStream**コンシューマーへのアクセスをサポートするインターフェイス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**、**テキスト**、**イメージ**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、および xml データ型とバイナリ ラージ オブジェクト (Blob)。 **読み取り**メソッド**ISequentialStream**コンシューマーが扱いやすい単位で多くのデータを取得することができます。  
  
 この機能を示すサンプルについては、次を参照してください。[大規模なデータの設定 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンシューマーに実装された Native Client OLE DB プロバイダーを使用して**IStorage**データ変更のため、コンシューマーはアクセサーのインターフェイス ポインターを提供するときのインターフェイスがバインドされています。  
  
 大きな値データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーで型の想定サイズをチェック**IRowset**や DDL インターフェイスです。 持つ列**varchar**、 **nvarchar**、および**varbinary**最大サイズが無制限に設定したデータ型がスキーマ行セットと列のデータ型を返すインターフェイスを通じて ISLONG として表されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **varchar (max)**、 **varbinary (max)**と**nvarchar (max)**それぞれ DBTYPE_STR、DBTYPE_BYTES、dbtype_wstr 型として型です。  
  
 アプリケーションではこれらの型を使用するには、次のオプションがあります。  
  
-   データ型 DBTYPE_STR、DBTYPE_BYTES、または DBTYPE_WSTR としてバインドします。 バッファーのサイズが十分でない場合、これらのデータ型は以前のリリースでの動作と同様に (以前よりも大きな値を格納できるようになりましたが)、切り捨てが行われます。  
  
-   データ型としてバインドし、DBTYPE_BYREF も指定します。  
  
-   DBTYPE_IUNKNOWN としてバインドし、ストリーミングを使用します。  
  
 DBTYPE_IUNKNOWN にバインドすると、ISequentialStream ストリーム機能が使用されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBTYPE_IUNKNOWN をストアド プロシージャがこれらのデータを返すシナリオを容易にする大きな値データ型は、クライアントに DBTYPE_IUNKNOWN として戻り値として公開されるを型としてバインドの出力パラメーターをサポートしています。  
  
## <a name="storage-object-limitations"></a>ストレージ オブジェクトの制限事項  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、単一の開いているストレージ オブジェクトのみをサポートできます。 1 つ以上のストレージ オブジェクトを開こうとすると (1 つ以上の参照を取得する**ISequentialStream**インターフェイス ポインター) DBSTATUS_E_CANTCREATE が返されます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、DBPROP_BLOCKINGSTORAGEOBJECTS の読み取り専用プロパティの既定値は VARIANT_TRUE です。 この値は、ストレージ オブジェクトがアクティブである場合に、(ストレージ オブジェクト以外の) 一部のメソッドが失敗して E_UNEXPECTED が返されることを示します。  
  
-   コンシューマーに実装されたストレージ オブジェクトによって提示されるデータの長さが正常に行う必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのストレージ オブジェクトを参照する行アクセサーの作成時にします。 コンシューマー側では、アクセサーの作成に使用する DBBINDING 構造体に長さのインジケーターをバインドする必要があります。  
  
-   コンシューマーを 1 つの大きなデータ値を超える行が含まれています、DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM ではない場合は、いずれかを使用する必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー カーソルでサポートされている行セットを行のデータを取得またはその他の行の値を取得する前にすべての大きなデータ値を処理します。 DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、任意の順序でアクセスできるように、バイナリ ラージ オブジェクト (Blob) としてすべての xml データ型をキャッシュします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [大きなデータの取得](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [大きなデータの設定](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [BLOB 出力パラメーターのストリーミング サポート](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [大きな値の型を使用します。](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
