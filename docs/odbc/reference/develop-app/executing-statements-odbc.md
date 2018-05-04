---
title: ODBC のステートメントを実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 09063f43-f5f0-4cf0-baa9-12fec8898997
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6815cfe6becac3f96854dcebd2a263b32266598e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="executing-statements-odbc"></a>ODBC ステートメントの実行
ODBC アプリケーションでは、SQL ステートメントを実行することによってほとんどすべてのデータベースへのアクセスを実行します。 イベントの全般的な順序では、ステートメント ハンドルを割り当て、ステートメント属性を設定、ステートメントを実行して、すべての結果を取得およびステートメント ハンドルを解放します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)  
  
-   [ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)  
  
-   [ステートメントの実行](../../../odbc/reference/develop-app/executing-a-statement.md)  
  
-   [ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)  
  
-   [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)  
  
-   [非同期実行 (通知方法)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)  
  
-   [ステートメント ハンドルの解放](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)
