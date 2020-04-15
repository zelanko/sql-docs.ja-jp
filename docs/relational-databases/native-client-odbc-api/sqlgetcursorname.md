---
title: カーソルを取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a9d81199840f59ec7ac4b9c94b0d58c86b9eab52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302156"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  アプリケーションでカーソル名が指定されていない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバは、カーソルの生成時にアプリケーション用のカーソル名を生成します。 アプリケーションは、位置指定された UPDATE ステートメントと DELETE ステートメントのドライバー定義のカーソル名を取得するのに**は、SQLGetCursorName**を使用できます。 アプリケーションは、位置指定データ操作ステートメントを利用するために**SQLSetCursorName**を呼び出す必要はありません。  
  
## <a name="see-also"></a>参照  
 [関数を取得します。](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
