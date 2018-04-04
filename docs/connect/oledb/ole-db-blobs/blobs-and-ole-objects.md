---
title: Blob と OLE オブジェクト |Microsoft ドキュメント
description: BLOB と OLE オブジェクト
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-blobs
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2afff6a5d9f19c0db2063ab0e0c486cc7460e971
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="blobs-and-ole-objects"></a>BLOB と OLE オブジェクト
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server を公開、 **ISequentialStream**コンシューマーへのアクセスをサポートするインターフェイス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ntext**、**テキスト**、**イメージ**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、および xml データ型とバイナリ ラージ オブジェクト (Blob)。 **読み取り**メソッド**ISequentialStream**コンシューマーが扱いやすい単位で多くのデータを取得することができます。  
  
 この機能を示すサンプルについては、次を参照してください。[大規模なデータの設定 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md)です。  
  
 コンシューマーに実装された、OLE DB Driver for SQL Server を使用できます**IStorage**データ変更のため、コンシューマーはアクセサーのインターフェイス ポインターを提供するときのインターフェイスがバインドされています。  
  
 大きな値データ型を OLE DB Driver for SQL Server 型での想定サイズのチェック**IRowset**や DDL インターフェイスです。 持つ列**varchar**、 **nvarchar**、および**varbinary**データ型および最大サイズが無制限に設定されてとして表されます ISLONG を通じて、スキーマ行セット列のデータ型を返すためのインターフェイス。  
  
 OLE DB Driver for SQL Server を公開、 **varchar (max)**、 **varbinary (max)**と**nvarchar (max)**それぞれ DBTYPE_STR、DBTYPE_BYTES、dbtype_wstr 型として型です。  
  
 このようなデータ型を使用して作業するために、アプリケーションでは次のような操作を行えます。  
  
-   データ型 DBTYPE_STR、DBTYPE_BYTES、または DBTYPE_WSTR としてバインドします。 場合は、バッファーの大きさがないための十分な切り捨てが行わ、以前のリリースでこれらの型と同様 (ただし、大きい値は、使用できるようになりました)。  
  
-   データ型としてバインドし、DBTYPE_BYREF も指定します。  
  
-   DBTYPE_IUNKNOWN としてバインドし、ストリーミングを使用します。  
  
 DBTYPE_IUNKNOWN にバインドすると、ISequentialStream ストリーム機能が使用されます。 SQL Server の OLE DB Driver には、大きな値データ型の DBTYPE_IUNKNOWN としてバインドの出力パラメーターがサポートしています。 これは、ストアド プロシージャが DBTYPE_IUNKNOWN としてクライアントに返されますの戻り値としてこれらのデータ型を返すシナリオをサポートします。  
  
## <a name="storage-object-limitations"></a>ストレージ オブジェクトの制限事項  
  
-   SQL Server の OLE DB Driver は、単一の開いているストレージ オブジェクトのみをサポートできます。 1 つ以上のストレージ オブジェクトを開こうとすると (1 つ以上の参照を取得する**ISequentialStream**インターフェイス ポインター) DBSTATUS_E_CANTCREATE が返されます。  
  
-   OLE DB Driver for SQL Server、DBPROP_BLOCKINGSTORAGEOBJECTS の読み取り専用プロパティの既定値は VARIANT_TRUE です。 そのため、ストレージ オブジェクトがアクティブな場合は、一部のメソッド (以外の記憶域オブジェクトのメソッド) 失敗して E_UNEXPECTED がします。  
  
-   コンシューマーに実装されたストレージ オブジェクトによって提示されるデータの長さできる必要既知 OLE DB Driver for SQL Server ストレージ オブジェクトを参照する行アクセサーの作成時にします。 コンシューマー側では、アクセサーの作成に使用する DBBINDING 構造体に長さのインジケーターをバインドする必要があります。  
  
-   行が含まれている場合より、1 つの大きなデータ値と DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM ではありません、コンシューマーを行のデータを取得またはその他の取得する前にすべての大きなデータ値を処理する、OLE DB Driver for SQL Server カーソルでサポートされている行セットを使用するか、必要があります。行の値。 DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM の場合は、SQL Server の OLE DB Driver は任意の順序でアクセスできるように、バイナリ ラージ オブジェクト (Blob) としてすべての xml データ型をキャッシュします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [大きなデータの取得](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [大きなデータの設定](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [BLOB 出力パラメーターのストリーミング サポート](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)        
 [大きな値の型を使用します。](../../oledb/features/using-large-value-types.md)  
  
  
