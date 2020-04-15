---
title: SQL セットストマウントオプション (デスクトップ データベース ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69b386aee3f95fd047f72510dce7658130ac7aa5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299412"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (デスクトップ データベース ドライバー)

|*オプション*|説明|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|非同期処理はサポートされていません。 fOption SQL_ASYNC_ENABLEは SQLSTATE S1C00 (ドライバが対応していない) を返します。|  
|SQL_KEYSET_SIZE|混合カーソルと動的カーソルはサポートされていないため、有効なキーセット・サイズは 0 のみです。 この値が他の値に設定されている場合、その値は 0 に変更され、呼び出しは SQL_SUCCESS_WITH_INFOおよび SQLSTATE 01S02 (オプション値が変更されました) を戻します。|  
|SQL_MAX_ROWS|デスクトップ データベース ドライバは返される行数の制限をサポートしていないため、有効な行セット のサイズは 0 のみです。 この値が他の値に設定されている場合、その値は 0 に変更され、呼び出しは SQL_SUCCESS_WITH_INFOおよび SQLSTATE 01S02 (オプション値が変更されました) を戻します。|  
|SQL_QUERY_TIMEOUT|サポートされていません。|  
|SQL_ROW_NUMBER|サポートされていません。|  
|SQL_SIMULATE_CURSOR|サポートされていません。|
