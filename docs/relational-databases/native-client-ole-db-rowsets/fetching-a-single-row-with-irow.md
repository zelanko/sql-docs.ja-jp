---
title: IRow による 1 行のフェッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b92878a8f847063e2a2bf18ee6bdaa6433de3d8b
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="fetching-a-single-row-with-irow"></a>IRow による 1 行のフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IRow**インターフェイスの実装、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パフォーマンスを向上させる Native Client OLE DB プロバイダーが簡素化されます。 **IRow**単一行オブジェクトの列に直接アクセスできます。 事前にわかっているコマンドの実行の結果が正確に 1 つの行を生成する場合**IRow**その行の列を取得します。 結果セットには、複数の行が含まれている場合**IRow**最初の行のみを公開します。  
  
 **IRow**実装では、行を移動することはできません。 行内の各列には 1 回だけアクセスされます。ただし、例外が 1 つあります。最初に列サイズを確認し、次にデータをフェッチする場合は、列に 2 回アクセスできます。  
  
> [!NOTE]  
>  **Irow::open**のみ DBGUID_STREAM 型と DBGUID_ 型のオブジェクトに開かれるをサポートしています。  
  
 使用して行オブジェクトを取得する**icommand::execute**メソッド、IID_IRow を渡す必要があります。 **IMultipleResults**インターフェイスは、複数の結果セットを処理するために使用する必要があります。 **IMultipleResults**サポート**IRow**と**IRowset**です。 **IRowset**一括操作のために使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IRow::GetColumns の使用](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [IRow を使用して BLOB データのフェッチ](http://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>参照  
 [行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
