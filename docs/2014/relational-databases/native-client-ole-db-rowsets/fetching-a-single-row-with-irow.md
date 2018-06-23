---
title: IRow による 1 行のフェッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eef27a6cbd6ee793cd227c2cf6e6570e1d04b004
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173702"
---
# <a name="fetching-a-single-row-with-irow"></a>IRow による 1 行のフェッチ
  **IRow**インターフェイスの実装、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パフォーマンスを向上させる Native Client OLE DB プロバイダーが簡素化されます。 **IRow**単一行オブジェクトの列に直接アクセスできます。 事前にわかっているコマンドの実行の結果が正確に 1 つの行を生成する場合**IRow**その行の列を取得します。 結果セットには、複数の行が含まれている場合**IRow**最初の行のみを公開します。  
  
 **IRow**実装では、行を移動することはできません。 行内の各列には 1 回だけアクセスされます。ただし、例外が 1 つあります。最初に列サイズを確認し、次にデータをフェッチする場合は、列に 2 回アクセスできます。  
  
> [!NOTE]  
>  **Irow::open**のみ DBGUID_STREAM 型と DBGUID_ 型のオブジェクトに開かれるをサポートしています。  
  
 使用して行オブジェクトを取得する**icommand::execute**メソッド、IID_IRow を渡す必要があります。 **IMultipleResults**インターフェイスは、複数の結果セットを処理するために使用する必要があります。 **IMultipleResults**サポート**IRow**と**IRowset**です。 **IRowset**一括操作のために使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IRow::GetColumns の使用](using-irow-getcolumns.md)  
  
-   [IRow を使用した BLOB データのフェッチ](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>参照  
 [行セット](rowsets.md)  
  
  