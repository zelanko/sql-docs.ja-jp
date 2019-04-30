---
title: データを挿入する SQLSetPos の呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c7424206318436532cad62690b01427f079a589
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63159274"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>データを挿入するための SQLSetPos の呼び出し
ODBC 2 時にします。*x* 、ODBC 3 の操作アプリケーション *.x*ドライバー呼び出し**SQLSetPos**で、*操作*SQL_ADD、ドライバー マネージャーの引数この呼び出しにマップされていない**SQLBulkOperations**します。 場合、ODBC 3 *.x*ドライバーを呼び出すアプリケーションを使用する必要があります**SQLSetPos** SQL_ADD で、ドライバーが操作をサポートする必要があります。  
  
 動作の 1 つの大きな違いと**SQLSetPos**を使用して呼び出した SQL_ADD は S6 の状態で呼び出された場合に発生します。 ODBC 2。*x*、ドライバーに返される S1010 とき**SQLSetPos**状態 S6 SQL_ADD で呼び出されました (後で、カーソルが位置付けられている**SQLFetch**)。 ODBC 3 *.x*、 **SQLBulkOperations**で、*操作*状態 S6 SQL_ADD の呼び出すことができます。 動作の 2 つ目の主要な違いは**SQLBulkOperations**で、*操作*SQL_ADD のできるは while S5 の状態で呼び出されると、 **SQLSetPos**で、 **操作**SQL_ADD のことはできません。 ODBC 3 内の同じ呼び出しで発生するステートメントの遷移の *.x*を参照してください[付録 b:ODBC の状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)します。
