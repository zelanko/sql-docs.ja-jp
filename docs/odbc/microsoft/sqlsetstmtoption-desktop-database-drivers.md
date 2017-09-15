---
title: "SQLSetStmtOption (デスクトップ データベース ドライバー) |Microsoft ドキュメント"
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
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d1f51805413056a06c6cee769920e1ad878abe5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (デスクトップ データベース ドライバー)
|*fOption*|コメント|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|非同期処理はサポートされていません。 SQL_ASYNC_ENABLE fOption は SQLSTATE S1C00 を返します (ドライバーを非対応)。|  
|SQL_KEYSET_SIZE|混合ために、唯一の有効なキーセットのサイズは 0、および動的カーソルはサポートされていません。 この値が他の任意の数に設定されている場合は 0 に変更し、呼び出しは SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 を返します (オプションの値が変更されました)。|  
|SQL_MAX_ROWS|唯一の有効な行セットのサイズは、デスクトップ データベース ドライバーが、返される行の数を制限することをサポートしていないために、0 です。 この値が他の任意の数に設定されている場合は 0 に変更し、呼び出しは SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 を返します (オプションの値が変更されました)。|  
|SQL_QUERY_TIMEOUT|サポートされていません。|  
|SQL_ROW_NUMBER|サポートされていません。|  
|SQL_SIMULATE_CURSOR|サポートされていません。|
