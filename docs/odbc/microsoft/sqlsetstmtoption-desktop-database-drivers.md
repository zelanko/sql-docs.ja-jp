---
title: SQLSetStmtOption (デスクトップ データベース ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b797d3eddb7eae9232aee3c73ceae7c12ca163d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
