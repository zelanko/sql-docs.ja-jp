---
title: SQLSetScrollOptions (デスクトップ データベース ドライバー) |Microsoft ドキュメント
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
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5838e890168473cd70d957eb1da6d4be45f546dc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902117"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (デスクトップ データベース ドライバー)
SQL_CONCUR_READ_ONLY では、順方向カーソルと静的カーソルはサポートされます。  
  
 キーセット ドリブン カーソルのみがサポートされている、 *fConcurrency* SQL_CONCUR_LOCK の引数。  
  
 *FConcurrency* SQL_CONCUR_ROWVER の引数はサポートされていません。  
  
 動的カーソルやカーソルの混合はサポートされていません。
