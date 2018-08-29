---
title: IRow による 1 行のフェッチ |Microsoft Docs
description: SQL Server 用の OLE DB Driver IRow インターフェイスを使用して 1 つの行をフェッチしています
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: b83b13e1cd0c4818a21351fb5433dae89f54cd0a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032357"
---
# <a name="fetching-a-single-row-with-irow"></a>IRow による 1 行のフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **IRow**インターフェイスの OLE DB driver の実装のパフォーマンスを向上させる SQL Server が簡略化されます。 **IRow** では、1 つの行オブジェクトの列に直接アクセスできます。 コマンドの実行結果が正確に 1 行になることが事前にわかっている場合、**IRow** でその行の列を取得できます。 結果セットが複数の行で構成される場合は、**IRow** では先頭の行だけが公開されます。  
  
 **IRow** 実装では、行を移動することはできません。 行内の各列には 1 回だけアクセスされます。ただし、例外が 1 つあります。最初に列サイズを確認し、次にデータをフェッチする場合は、列に 2 回アクセスできます。  
  
> [!NOTE]  
>  **IRow::Open** は、DBGUID_STREAM 型と DBGUID_NULL 型のオブジェクトを開くことだけをサポートします。  
  
 **ICommand::Execute** メソッドを使用して行オブジェクトを取得するには、IID_IRow を渡す必要があります。 複数の結果セットを処理するには、**IMultipleResults** インターフェイスを使用する必要があります。 **IMultipleResults** では、**IRow** と **IRowset** がサポートされます。 **IRowset** は、一括操作に使用されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IRow::GetColumns の使用](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
