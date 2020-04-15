---
title: SQL セットストマウントオプション (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299402"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 ステートメント ハンドル*hstmt*に関連するオプションを設定します。  
  
|*オプション*|使用できる値|説明|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|この*fOption*を設定しようとすると、ドライバーはエラーを返します: "ドライバーができません"。 ビジュアル フォックスプロは非同期実行をサポートしていません。|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMNまたは 32 ビット値は、結果列がバインドされるバッファーの構造体またはインスタンスの長さを示します。||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Visual FoxPro にはタイムスタンプに基づく行のバージョン管理がないため、ドライバはSQL_CONCUR_ROWVERを許可しません。|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|ドライバーは、SQL_CURSOR_KEYSET_DRIVENまたはSQL_CURSOR_DYNAMICを許可しません。詳細については[、「スクロール オプション](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md)」を参照してください。|  
|SQL_KEYSET_SIZE|エラー: "ドライバが使用できません"|ビジュアル FoxPro はキーセット カーソル モデルをサポートしていません。|  
|SQL_MAX_LENGTH|0|この*fOption*値を設定しようとすると、ドライバーはエラー "ドライバーができません" を返します。|  
|SQL_MAX_ROWS|0|この*fOption*値を設定しようとすると、ドライバーはエラー "ドライバーができません" を返します。|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|この*fOption*値を設定しようとすると、ドライバーはエラー "ドライバーができません" を返します。|  
|SQL_RETRIEVE_DATA|SQL_RD_ON、SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1~ 4,294,967,296||  
|SQL_SIMULATE_CURSOR|エラー: "ドライバが使用できません"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 詳細については *、ODBC プログラマ リファレンス*の「 [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) 」を参照してください。
