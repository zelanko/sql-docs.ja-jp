---
title: "C データ型の下位互換性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c7c999230837dcb78a294ab2f1b462c6932ab3a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="backward-compatibility-of-c-data-types"></a>C データ型の旧バージョンとの互換性
SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT に置換された ODBC の符号付きと符号なしの型: SQL_C_SSHORT と SQL_C_USHORT、SQL_C_SLONG、SQL_C_ULONG、and SQL_C_STINYINT SQL_C_UTINYINT です。 ODBC 3*.x* ODBC 2 で動作するドライバー *。x*アプリケーションは、そのため、呼び出されるときに、ドライバー マネージャーを使ってドライバーに渡します SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT、サポートする必要があります。
