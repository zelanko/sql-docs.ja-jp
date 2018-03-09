---
title: "データを挿入する SQLSetPos を呼び出して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b5705fe7c5004a2c1e5845b3639c51681b046e2c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="calling-sqlsetpos-to-insert-data"></a>データを挿入する SQLSetPos を呼び出す
ODBC 2 時にします。*x* ODBC 3 作業アプリケーション*.x*ドライバー呼び出し**SQLSetPos**で、*操作*SQL_ADD、ドライバー マネージャーの引数この呼び出しにマップされていない**SQLBulkOperations**です。 場合、ODBC 3*.x*ドライバーを呼び出すアプリケーションでは動作する必要があります**SQLSetPos**ドライバーは、SQL_ADD でその操作をサポートする必要があります。  
  
 動作の 1 つの主な違いと**SQLSetPos**で呼び出された SQL_ADD は S6 の状態で呼び出された場合に発生します。 ODBC 2 です。*x*、ドライバーに返される S1010 とき**SQLSetPos**状態 S6 SQL_ADD で呼び出されました (後で、カーソルが位置付けられている**SQLFetch**)。 ODBC 3*.x*、 **SQLBulkOperations**で、*操作*SQL_ADD の状態 S6 で呼び出すことができます。 動作の 2 つ目の主な相違点は**SQLBulkOperations**で、*操作*SQL_ADD のできるは while S5 の状態で呼び出されると、 **SQLSetPos**で、 **操作**SQL_ADD のことはできません。 ODBC 3 内の同じ呼び出しで発生するステートメントの遷移*.x*を参照してください[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。
