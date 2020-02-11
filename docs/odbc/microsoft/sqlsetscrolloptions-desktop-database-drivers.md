---
title: SQLSetScrollOptions (デスクトップデータベースドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0adedfb69cd4a7b5cf195916747687826805e8bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905390"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (デスクトップ データベース ドライバー)
SQL_CONCUR_READ_ONLY では、転送カーソルと静的カーソルがサポートされています。  
  
 SQL_CONCUR_LOCK の*Fconcurrency*引数では、キーセットドリブンカーソルのみがサポートされています。  
  
 SQL_CONCUR_ROWVER の*Fconcurrency*引数はサポートされていません。  
  
 動的カーソルおよび混合カーソルはサポートされていません。
