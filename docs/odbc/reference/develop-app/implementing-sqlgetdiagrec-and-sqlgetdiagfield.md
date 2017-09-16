---
title: "SQLGetDiagRec および SQLGetDiagField を実装する |Microsoft ドキュメント"
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 463ddfe552c94a9e90ceb2a24f8061674955979d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>SQLGetDiagRec および SQLGetDiagField を実装します。
**SQLGetDiagRec**と**SQLGetDiagField**と各ドライバーのドライバー マネージャーによって実装されます。 ドライバー マネージャーと各ドライバーは、各環境、接続、ステートメント、および記述子ハンドルに対する診断レコードを維持してハンドルまたはハンドルが解放されていることを別の関数が呼び出されたときにのみ、これらのレコードを解放します。  
  
 ドライバー マネージャーと各ドライバーの両方でランク付けに従って最初の状態レコードを決定する必要がありますが[状態レコードのシーケンス](../../../odbc/reference/develop-app/sequence-of-status-records.md)、ドライバー マネージャーは、レコードの最後のシーケンスを決定します。  
  
 **SQLGetDiagRec**と**SQLGetDiagField**自体についての診断レコードを送信しません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [診断の処理ルール](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [ドライバー マネージャーの役割](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [ドライバーのロール](../../../odbc/reference/develop-app/role-of-the-driver.md)
