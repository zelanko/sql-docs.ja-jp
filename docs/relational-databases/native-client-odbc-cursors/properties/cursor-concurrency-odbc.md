---
title: カーソルの同時実行 (ODBC) |Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e3ed3e4397f5a8713865849a0100ac0800a760ba
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006522"
---
# <a name="cursor-concurrency-odbc"></a>カーソル コンカレンシー (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  カーソル操作は、カーソルの種類と同様に、アプリケーションで設定されるコンカレンシー オプションの影響を受けます。 同時実行オプションは、 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)の SQL_ATTR_CONCURRENCY オプションを使用して設定します。 コンカレンシーの種類は次のとおりです。  
  
-   読み取り専用 (SQL_CONCUR_READONLY)  
  
-   値 (SQL_CONCUR_VALUES)  
  
-   行バージョン (SQL_CONCUR_ROWVER)  
  
-   ロック (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
