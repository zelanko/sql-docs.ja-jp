---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc8a8cac364c9226d32ed2ebadbc2702e13031ab
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298455"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  手動コミットモードでは、トランザクションが開いているステートメントハンドルで**Sqlfreehandle**を呼び出すと、データベースに対する保留中の変更がロールバックされます。 ステートメントハンドルで**Sqlfreehandle**を呼び出すと、開いているカーソルが常に閉じられ、保留中の結果は破棄され、ステートメントハンドルに関連付けられているすべてのリソースが解放されます。  
  
## <a name="see-also"></a>参照  
 [SQLFreeHandle 関数](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
