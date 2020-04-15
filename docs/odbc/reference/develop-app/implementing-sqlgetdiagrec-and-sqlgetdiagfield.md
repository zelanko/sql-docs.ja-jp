---
title: SQL を実装する場合は、次の手順を実行します。マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c090af19a9296e46e3036ca23f6c97298bcb1b8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300142"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>SQLGetDiagRec および SQLGetDiagField の実装
**ドライバー マネージャー****と各**ドライバーによって実装されます。 ドライバー マネージャーと各ドライバーは、各環境、接続、ステートメント、および記述子ハンドルの診断レコードを保持し、別の関数がそのハンドルを呼び出すか、ハンドルが解放された場合にのみ、それらのレコードを解放します。  
  
 ドライバー マネージャーと各ドライバーの両方が、状態レコードのシーケンスのランキングに従って最初[の状態レコード](../../../odbc/reference/develop-app/sequence-of-status-records.md)を決定する必要がありますが、ドライバー マネージャーは、レコードの最終的なシーケンスを決定します。  
  
 **SQLGetDiagRec**と**SQLGetDiagField**は、自分自身に関する診断レコードをポストしません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [診断の処理規則](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [ドライバー マネージャーのロール](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [ドライバーのロール](../../../odbc/reference/develop-app/role-of-the-driver.md)
