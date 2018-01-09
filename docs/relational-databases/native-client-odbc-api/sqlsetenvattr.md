---
title: "SQLSetEnvAttr |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51d535d938bfd4e0e70ae12537b40bdb76665e54
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [ODBC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=45250)ODBC ドライバーを解釈する方法を定義、 **SQLSetEnvAttr**属性のいずれか、ODBC 2 に記述されたアプリケーションからの仕様*。x*または ODBC 3 *。x* API です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、これらの規則に準拠しています。  
  
 によって制御される属性のいずれかの**SQLSetEnvAttr**が使用するかどうかが接続プールします。 接続プールを使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、 *DriverCompletion*パラメーターは、いずれかで接続するときに SQL_DRIVER_NOPROMPT を設定する必要があります[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)または**SQLConnect**です。  
  
## <a name="see-also"></a>参照  
 [SQLSetEnvAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
