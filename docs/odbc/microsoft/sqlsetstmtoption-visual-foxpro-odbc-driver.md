---
title: SQLSetStmtOption (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb9677a9ccf307be847089c657964d96904eb20b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299402"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: レベル1  
  
 ステートメントハンドルの*hstmt*に関連するオプションを設定します。  
  
|*fOption*|使用できる値|説明|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|この*Foption*を設定しようとすると、ドライバーは "ドライバーがサポートされていません" というエラーを返します。 Visual FoxPro では、非同期実行はサポートされていません。|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN または結果列がバインドされるバッファーの構造体またはインスタンスの長さを示す32ビット値。||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Visual FoxPro ではタイムスタンプに基づいて行のバージョン管理が行われないため、ドライバーは SQL_CONCUR_ROWVER を許可しません。|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|ドライバーで SQL_CURSOR_KEYSET_DRIVEN または SQL_CURSOR_DYNAMIC が許可されていません。詳細については、「 [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) 」を参照してください。|  
|SQL_KEYSET_SIZE|エラー: "ドライバーに対応していません"|Visual FoxPro では、keyset カーソルモデルはサポートされていません。|  
|SQL_MAX_LENGTH|0|この*Foption*値を設定しようとすると、ドライバーは "ドライバーがサポートされていません" というエラーを返します。|  
|SQL_MAX_ROWS|0|この*Foption*値を設定しようとすると、ドライバーは "ドライバーがサポートされていません" というエラーを返します。|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|この*Foption*値を設定しようとすると、ドライバーは "ドライバーがサポートされていません" というエラーを返します。|  
|SQL_RETRIEVE_DATA|SQL_RD_ON、SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 ~ 4294967296||  
|SQL_SIMULATE_CURSOR|エラー: "ドライバーに対応していません"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) 」を参照してください。
