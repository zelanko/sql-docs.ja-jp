---
title: SQLSetScrollOptions (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19051fc83466bc40d72c029089cfe6ec45c20a08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299422"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 部分的  
  
 ODBC API の準拠: レベル2  
  
 ステートメントハンドルの*hstmt*に関連付けられているカーソルの動作を制御するオプションを設定します。  
  
 Visual FoxPro ODBC ドライバーでは、SQL_CONCUR_READ_ONLY のみがサポートされます。*Fconcurrency*値 SQL_CONCUR_ROWVER はサポートされていません。 ドライバーは、SQL_KEYSET_SIZE、SQL_CURSOR_DYNAMIC、および SQL_CURSOR_KEYSET_DRIVEN を警告 ODBC_01S02 と共に SQL_SCROLL_STATIC に変換します。  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) 」を参照してください。
