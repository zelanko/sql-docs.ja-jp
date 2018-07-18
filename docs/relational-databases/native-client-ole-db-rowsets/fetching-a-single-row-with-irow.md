---
title: IRow による 1 行のフェッチ |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ab4a6e50ce20b1bceddfb639e5780938f3687639
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412001"
---
# <a name="fetching-a-single-row-with-irow"></a>IRow による 1 行のフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IRow**インターフェイスの実装、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがパフォーマンスを向上する簡略化されます。 **IRow**単一行オブジェクトの列に直接アクセスできます。 事前にわかっているコマンドの実行の結果が正確に 1 つの行を生成する場合**IRow**その行の列を取得します。 結果セットに複数の行が含まれている場合**IRow**最初の行だけが公開されます。  
  
 **IRow**実装では、行を移動することはできません。 行内の各列には 1 回だけアクセスされます。ただし、例外が 1 つあります。最初に列サイズを確認し、次にデータをフェッチする場合は、列に 2 回アクセスできます。  
  
> [!NOTE]  
>  **Irow::open**のみ DBGUID_STREAM 型と DBGUID_ 型のオブジェクトを開くをサポートしています。  
  
 使用して行オブジェクトを取得する**icommand::execute**メソッド、IID_IRow を渡す必要があります。 **IMultipleResults**インターフェイスを使用して、複数の結果セットを処理する必要があります。 **IMultipleResults**サポート**IRow**と**IRowset**します。 **IRowset**の一括操作で使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IRow::GetColumns の使用](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [IRow を使用した BLOB データのフェッチ](http://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>参照  
 [行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
