---
title: テキストおよびイメージ データを一括 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5a8c6a70a4d1682117fff68cefe38f5d40a1e5d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bulk-copying-text-and-image-data"></a>テキスト データと画像データの一括コピー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  大規模な**テキスト**、 **ntext**、および**イメージ**値は、一括コピーを使用して、 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)関数。 コードを記述[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)の**テキスト**、 **ntext**、または**イメージ**列が、 *pData*ポインターに設定NULL を示すデータが提供されます**bcp_moretext**です。 各入力データの正確な長さを指定することが重要**テキスト**、 **ntext**、または**イメージ**一括コピーの各行の列です。 列のデータの長さがで指定された列の長さと異なる場合[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を使用して[bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)長さを適切な値に設定します。 A [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)送信すべて、非**テキスト**、非-**ntext**、および非-**イメージ**データ以外の場合は、呼び出す**bcp_moretext**を送信する、**テキスト**、 **ntext**、または**イメージ**個別の単位でのデータ。 一括コピー関数では、現在のすべてのデータが送信されたことを確認**テキスト**、 **ntext**、または**イメージ**を介して送信されるデータの長さの合計列**bcp_moretext**最新で指定された長さに等しくなる**bcp_collen**または**bcp_bind**です。  
  
 **bcp_moretext**列を識別するパラメーターがありません。 複数あるときに**テキスト**、 **ntext**、または**イメージ**、行を列に**bcp_moretext**を演算し、**テキスト**、 **ntext**、または**イメージ**最高の序数の列を続行するポート番号と最小の序数を持つ列から始まる列です。 **bcp_moretext**が 1 つの列からに、次へ送信されるデータの長さの合計が最新で指定された長さと**bcp_collen**または**bcp_bind**現在の列です。  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
