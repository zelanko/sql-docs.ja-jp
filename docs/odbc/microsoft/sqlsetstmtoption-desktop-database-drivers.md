---
title: SQLSetStmtOption (デスクトップ データベース ドライバー) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48dc5dff83e942b894548d44e3673c19ca0746c5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305788"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (デスクトップ データベース ドライバー)

|*fOption*|コメント|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|非同期処理がサポートされていません。 SQL_ASYNC_ENABLE fOption は SQLSTATE S1C00 を返します (ドライバーに対応していない)。|  
|SQL_KEYSET_SIZE|混在しているために、唯一の有効なキーセットのサイズは 0、および動的カーソルはサポートされていません。 この値が他の任意の数に設定されている場合は 0 に変更して、呼び出しは SQL_SUCCESS_WITH_INFO および SQLSTATE 01S02 を返します (オプションの値が変更されました)。|  
|SQL_MAX_ROWS|唯一の有効な行セットのサイズは、デスクトップ データベース ドライバーが返される行の数の制限をサポートしていないために、0 です。 この値が他の任意の数に設定されている場合は 0 に変更して、呼び出しは SQL_SUCCESS_WITH_INFO および SQLSTATE 01S02 を返します (オプションの値が変更されました)。|  
|SQL_QUERY_TIMEOUT|サポートされていません。|  
|SQL_ROW_NUMBER|サポートされていません。|  
|SQL_SIMULATE_CURSOR|サポートされていません。|
