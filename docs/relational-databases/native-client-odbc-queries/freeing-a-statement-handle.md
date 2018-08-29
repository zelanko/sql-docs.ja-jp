---
title: ステートメント ハンドルの解放 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a82c5dca156d7f3c10f7854d2ea147890921ae01
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102709"
---
# <a name="freeing-a-statement-handle"></a>ステートメント ハンドルの解放
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ステートメント ハンドルは、削除して新しいハンドルを割り当てるよりも、再利用する方が効率的です。 アプリケーションでは、任意のステートメント ハンドルで新しい SQL ステートメントを実行する前に、現在のステートメント設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 一般に、パラメーターと結果を設定します、古い SQL ステートメントを呼び出すことによってバインド解除する必要があります[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) SQL_RESET_PARAMS と SQL_UNBIND オプションし、新しい SQL ステートメントの再バインドします。  
  
 呼び出しステートメントを使用するが、アプリケーションが完了したら、 [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)ステートメントを解放します。 なお**SQLDisconnect**接続ですべてのステートメントを自動的に解放します。  
  
## <a name="see-also"></a>参照  
 [クエリの実行&#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
