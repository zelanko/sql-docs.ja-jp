---
title: "診断 |Microsoft ドキュメント"
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
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: adb6f66ecfbff558fd163437a56453efb4265185
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="diagnostics"></a>診断
Odbc 関数では、2 つの方法で診断情報を返します。 リターン コードでは、診断レコードが、関数に関する詳細情報を提供中に、全体の成功または失敗、関数を示します。 少なくとも 1 つの診断レコード — ヘッダー レコード: 関数が成功した場合でも返されます。  
  
 診断情報は、ハード コーディングされた SQL ステートメントで無効なハンドルなどのプログラミング エラーや構文エラーをキャッチする開発時に使用されます。 ユーザーが入力した SQL ステートメントの実行時エラーとデータの切り捨て、アクセス違反、構文エラーなどの警告をキャッチする実行時に使用されます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [リターン コード](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [診断レコード](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField を使用してください。](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField を実装します。](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [診断の処理の例](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
