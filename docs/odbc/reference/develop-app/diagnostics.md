---
title: 診断 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a09f46d3fd6aa2f9b9c7310af6d3ddc90f78389f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305153"
---
# <a name="diagnostics"></a>診断
ODBC の関数は、2 つの方法で診断情報を返します。 戻りコードは関数の全体的な成功または失敗を示し、診断レコードは関数に関する詳細情報を提供します。 関数が成功した場合でも、少なくとも 1 つの診断レコード (ヘッダー レコード) が返されます。  
  
 診断情報は、ハードコーディングされた SQL ステートメントでの無効なハンドルや構文エラーなどのプログラミング エラーを検出するために、開発時に使用されます。 実行時に、実行時に、実行時に、データの切り捨て、アクセス違反、およびユーザーが入力した SQL ステートメントの構文エラーなどの警告をキャッチするために使用されます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [リターン コード](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [診断レコード](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField の使用](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField の実装](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [診断処理の例](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
