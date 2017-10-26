---
title: "SQLSetScrollOptions (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63efd04bc43855c08a6de02d5396bea45eabbc68
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 部分的な  
  
 ODBC API への準拠: レベル 2  
  
 ステートメント ハンドルに関連付けられているカーソルの動作を制御するオプションを設定*hstmt*です。  
  
 Visual FoxPro ODBC ドライバーは、のみ SQL_CONCUR_READ_ONLY; をサポートしています。サポートされていません、 *fConcurrency* SQL_CONCUR_ROWVER の値します。 ドライバーは SQL_KEYSET_SIZE、SQL_CURSOR_DYNAMIC、および SQL_CURSOR_KEYSET_DRIVEN を警告 ODBC_01S02 SQL_SCROLL_STATIC に変換します。  
  
 詳細については、次を参照してください。 [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)で、 *ODBC プログラマ リファレンス*です。

