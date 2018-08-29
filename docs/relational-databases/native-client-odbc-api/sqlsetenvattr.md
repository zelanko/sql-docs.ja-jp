---
title: SQLSetEnvAttr |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b086b62e7241e3bb82b3d85fe7e83720c575d6a5
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084323"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [ODBC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=45250)ODBC ドライバーを解釈する方法を定義、 **SQLSetEnvAttr**属性の ODBC 2 に書かれたアプリケーションからの仕様 *。x*または ODBC 3 *。x* API。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、これらの規則に準拠します。  
  
 によって制御される属性の 1 つ**SQLSetEnvAttr**は使用するかどうかが接続プールします。 接続プールを使用した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、 *DriverCompletion*いずれかで接続するときに、パラメーターを SQL_DRIVER_NOPROMPT に設定する必要があります[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)または**SQLConnect**します。  
  
## <a name="see-also"></a>参照  
 [SQLSetEnvAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
