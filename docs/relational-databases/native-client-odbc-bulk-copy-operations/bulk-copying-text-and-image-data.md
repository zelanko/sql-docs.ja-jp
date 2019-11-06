---
title: テキストとイメージデータを一括コピーする |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5243c862e07ad8b4f5a0b3b33ea292cecc1cb0a9
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707906"
---
# <a name="bulk-copying-text-and-image-data"></a>テキスト データと画像データの一括コピー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Large **text**、 **ntext**、 **image**の値は、 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)関数を使用して一括コピーされます。 **Text**、 **ntext**、または**image**型の列に対して[Bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)をコードに記述し、 *pData*ポインターを NULL に設定して、データが**bcp_moretext**によって提供されることを示します。 各一括コピーされた行の**text**、 **ntext**、または**image**列ごとに指定されるデータの正確な長さを指定することが重要です。 列のデータの長さが、 [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)で指定された列の長さと異なる場合は、 [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)を使用して長さを適切な値に設定します。 [Bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)は、すべての非**テキスト**、非**ntext**、**画像**以外のデータを送信します。次に、 **bcp_moretext**を呼び出して、 **text**、 **ntext**、または**image**型のデータを個別の単位で送信します。 一括コピー関数は、 **bcp_moretext**から送信されたデータの長さの合計が、最新の bcp_collen で指定された長さと等しい場合に、現在の**text**、 **ntext**、または**image**列に対してすべてのデータが送信されたことを確認します。または**bcp_bind**。  
  
 **bcp_moretext**には、列を識別するパラメーターがありません。 行内に複数の**text**、 **ntext**、または**image**型の列がある場合、 **bcp_moretext**は、最も小さい序数を持つ列で始まる**text**、 **ntext**、または**image**型の列を操作します。序数が最も大きい列に進みます。 **bcp_moretext**は、送信されるデータの長さの合計が、現在の列の最新の**bcp_collen**または**bcp_bind**で指定された長さと同じ場合に、1つの列から次の列に移動します。  
  
## <a name="see-also"></a>関連項目  
 [一括コピー操作&#40;の実行 (ODBC)&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
