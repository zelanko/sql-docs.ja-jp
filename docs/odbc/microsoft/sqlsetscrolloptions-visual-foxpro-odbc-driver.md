---
title: スクロールオプション ( ビジュアル フォックスプロ ODBC ドライバー ) |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299422"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: 部分  
  
 ODBC API 準拠: レベル 2  
  
 ステートメント ハンドル*hstmt*に関連付けられたカーソルの動作を制御するオプションを設定します。  
  
 ビジュアル フォックスプロ ODBC ドライバーはSQL_CONCUR_READ_ONLYのみをサポートします。*f同時実行*値SQL_CONCUR_ROWVERはサポートしていません。 ドライバーは、警告ODBC_01S02をSQL_SCROLL_STATICにSQL_KEYSET_SIZE、SQL_CURSOR_DYNAMIC、およびSQL_CURSOR_KEYSET_DRIVENを変換します。  
  
 詳細については *、ODBC プログラマ リファレンス*の「 [SQLSetScrollOptions」](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)を参照してください。
