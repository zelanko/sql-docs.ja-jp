---
title: "機能のサポートとばらつきを確認しています |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31b297b5d1932c6e3a9c8b7e128973d36fbd93cd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="checking-feature-support-and-variability"></a>機能のサポートとばらつきを確認しています
アプリケーション機能のサポートとばらつきを確認する呼び出し通常**SQLGetInfo**、 **SQLGetFunctions**、および**SQLGetTypeInfo**です。 開始点としては、ドライバーの API と SQL の文法の準拠レベルです。 これらのさまざまなレベルの機能サポートについて説明します。 アプリケーションが呼び出すことができますし、 **SQLGetInfo**サポートまたは必要な機能の違いを確認するには、他のオプションと**SQLGetFunctions**を決定するかどうか、返された以外に必要な関数準拠レベルがサポートされている、および**SQLGetTypeInfo**をどのような SQL データ型がサポートされているかを判断します。  
  
 アプリケーションでは、呼び出すことによって、ステートメントまたは接続属性がサポートされているかどうかを判断できます**SQLSetStmtAttr**または**SQLSetConnectAttr**その属性を持つ。 関数から SQL_SUCCESS または sql_success_with_info が返された場合、属性はサポートされています。SQLSTATE HYC00 SQL_ERROR を返す場合 (省略可能な機能で実装されていません)、属性はサポートされていません。  
  
 アプリケーションは、呼び出すことによって、ドライバーに接続する前に、情報量が限られても特定できます**SQLDrivers**です。
