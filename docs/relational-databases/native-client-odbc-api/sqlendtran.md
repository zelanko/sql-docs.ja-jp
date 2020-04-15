---
title: SQL エンドラン |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f2c4851b4cbb88c0d927aa4739e06501ce5ca1b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298512"
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは **、SQLEndTran**が操作をコミットまたはロールバックするときに、ステートメントの関連付けられたカーソルを閉じます。 サーバー カーソルは、静的カーソルでない限り、閉じられます。 **SQLEndTran が**操作をコミットまたはロールバックする場合、ステートメントに関連付けられたカーソルの動作は[、SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)によって設定された、ドライバー固有の ODBC 接続属性SQL_COPT_SS_PRESERVE_CURSORSの値によって決定されます。  
  
## <a name="see-also"></a>参照  
 [ODBC API の実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLEndTran 関数](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
