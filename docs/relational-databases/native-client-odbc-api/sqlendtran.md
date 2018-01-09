---
title: "SQLEndTran |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords: SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 68a3d0f6df87f316e3bf2055365aa09493135b97
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはステートメントの関連付けられたカーソルを閉じるときに**SQLEndTran**がコミットまたはロールバック操作します。 サーバー カーソルは、静的カーソルでない限り、閉じられます。 ときに**SQLEndTran**がコミットまたはロールバック操作、ステートメントの関連付けられたカーソルの動作はによって設定ドライバー固有のODBC接続属性SQL_COPT_SS_PRESERVE_CURSORSの値によって決まります[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLEndTran 関数](http://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
