---
title: バインドされたテキストとイメージの列のバインドと非バインドの値 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0cfa05f7019342d63ab6f3092c3b6df5ae6e8daa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297740"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>バインドされた text、image 型の列とバインドされない text、image 型の列
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  サーバー カーソルを使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ネイティブ クライアント ODBC ドライバは **、SQLFetch**の実行時に非連結**テキスト****、ntext、** または**image**列のデータを送信しないように最適化されます。 **テキスト**、 **ntext**、または**イメージ**のデータは、アプリケーションが列に対して[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)を発行するまで、実際にはサーバーから取得されません。  
  
 多くのアプリケーションを記述して、ユーザーがカーソル内をスクロールしている間、**テキスト****、ntext、** または**image**データが表示されないようにすることができます。 ユーザーが行を選択して詳細を取得すると、アプリケーションは**SQLGetData**を呼び出して**テキスト** **、ntext**、または**イメージ**データを取得できます。 これにより、ユーザーが選択しない行の**テキスト****、ntext、** または**image**データが送信されなくなり、大量のデータが送信されないようにすることができます。  
  
## <a name="see-also"></a>参照  
 [テキストとイメージの列の管理](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [カーソル動作](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
