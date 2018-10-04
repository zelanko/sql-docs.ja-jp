---
title: カーソルの同時実行 (ODBC)。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5c11ee87fe49e13bddd1a4331258a412916373b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666036"
---
# <a name="cursor-concurrency-odbc"></a>カーソル コンカレンシー (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  カーソル操作は、カーソルの種類と同様に、アプリケーションで設定されるコンカレンシー オプションの影響を受けます。 同時実行オプションが設定の SQL_ATTR_CONCURRENCY オプションを使用して[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)します。 コンカレンシーの種類は次のとおりです。  
  
-   読み取り専用 (SQL_CONCUR_READONLY)  
  
-   値 (SQL_CONCUR_VALUES)  
  
-   行バージョン (SQL_CONCUR_ROWVER)  
  
-   ロック (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
