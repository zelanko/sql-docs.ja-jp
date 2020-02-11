---
title: SQLSetStmtOption (デスクトップデータベースドライバー) |Microsoft Docs
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
ms.openlocfilehash: 20043c96771bf888defa2c8fbeb028aaa18f5abc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905342"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (デスクトップ データベース ドライバー)

|*fOption*|説明|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|非同期処理はサポートされていません。 SQL_ASYNC_ENABLE fOption は SQLSTATE S1C00 (ドライバーに対応していません) を返します。|  
|SQL_KEYSET_SIZE|混合カーソルと動的カーソルはサポートされていないため、有効なキーセットサイズは0のみです。 この値を他の数値に設定すると、0に変更され、呼び出しは SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 (オプション値が変更されました) を返します。|  
|SQL_MAX_ROWS|デスクトップデータベースドライバーでは、返される行の数の制限はサポートされていないため、有効な行セットのサイズは0だけです。 この値を他の数値に設定すると、0に変更され、呼び出しは SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 (オプション値が変更されました) を返します。|  
|SQL_QUERY_TIMEOUT|サポートされていません。|  
|SQL_ROW_NUMBER|サポートされていません。|  
|SQL_SIMULATE_CURSOR|サポートされていません。|
