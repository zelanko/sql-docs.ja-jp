---
title: テキストとイメージ データの一括コピー |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
ms.openlocfilehash: f647e9dae0a54bfb35ff9b0868891e74cfd7d125
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416711"
---
# <a name="bulk-copying-text-and-image-data"></a>テキスト データと画像データの一括コピー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  大規模な**テキスト**、 **ntext**、および**イメージ**値は、一括コピーを使用して、 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)関数。 コードを記述[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)の**テキスト**、 **ntext**、または**イメージ**列で、 *pData*ポインターに設定NULL を示すデータが提供されます**bcp_moretext**します。 それぞれの指定したデータの正確な長さを指定することが重要**テキスト**、 **ntext**、または**イメージ**一括コピーの各行の列。 列のデータの長さがで指定された列の長さと異なる場合[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を使用して、 [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)長さを適切な値に設定します。 A [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)送信すべて以外**テキスト**、非-**ntext**、および非-**イメージ**データは呼び出して**bcp_moretext**を送信する、**テキスト**、 **ntext**、または**イメージ**個別の単位でのデータ。 一括コピー関数は、現在のすべてのデータが送信されたことを確認**テキスト**、 **ntext**、または**イメージ**を通じて送信されるデータの長さの合計列**bcp_moretext**最新版の指定された長さと等しい**bcp_collen**または**bcp_bind**します。  
  
 **bcp_moretext**列を識別するためにパラメーターがありません。 複数の場合**テキスト**、 **ntext**、または**イメージ**、行内の列**bcp_moretext**で動作、**テキスト**、 **ntext**、または**イメージ**列序数が最も低い、最高の序数の列に進みますから始まる列。 **bcp_moretext**送信されるデータの長さの合計が最新で指定された長さと等しい場合は、次 1 つの列からが**bcp_collen**または**bcp_bind**現在の列。  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
