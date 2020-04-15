---
title: 記述子ハンドル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application parameter descriptor [ODBC]
- automatically allocated descriptors [ODBC]
- implementation row descriptor [ODBC]
- descriptor handles [ODBC]
- handles [ODBC], descriptor
- implementation parameter descriptor [ODBC]
- apd [ODBC]
- ard [ODBC]
- explicitly allocated descriptors [ODBC]
- ipd [ODBC]
- ird [ODBC]
- application row descriptor [ODBC]
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed0595c97f3f4ad92d976c89327a01e25cb5b753
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305913"
---
# <a name="descriptor-handles"></a>記述子ハンドル
*記述子*は、アプリケーションまたはドライバー (*実装*とも呼ばれます) によって見られるように、SQL ステートメントのパラメーターまたは結果セットの列を記述するメタデータのコレクションです。 したがって、記述子は次の 4 つのロールを満たすことができます。  
  
-   **アプリケーション パラメータ記述子 (APD)。** SQL ステートメントのパラメーターにバインドされているアプリケーション・バッファー (アドレス、長さ、C データ・タイプなど) に関する情報を含みます。  
  
-   **実装パラメータ記述子 (IPD)。** SQL ステートメントのパラメーターに関する情報 (SQL データ・タイプ、長さ、および NULL 許容など) が含まれます。  
  
-   **アプリケーション行記述子 (ARD)。** 結果セット内の列にバインドされているアプリケーション バッファーに関する情報 (アドレス、長さ、C データ型など) が含まれます。  
  
-   **実装行記述子 (IRD)。** SQL データ型、長さ、NULL 値の許容値など、結果セット内の列に関する情報を格納します。  
  
 ステートメントが割り当てられると、4 つの記述子 (各ロールを満たす記述子) が自動的に割り当てられます。 これらは*自動的に割り当てられた記述子*として知られ、常にそのステートメントに関連付けられます。 アプリケーションは**SQLAllocHandle**を使用して記述子を割り当てることもできます。 これらは明示的*に割り当てられた記述子*と呼ばれます。 これらは接続に割り当てられ、その接続上の 1 つ以上のステートメントに関連付けて、それらのステートメントで APD または ARD の役割を果たすことができます。  
  
 ODBC のほとんどの操作は、アプリケーションで記述子を明示的に使用しなくても実行できます。 ただし、記述子は、一部の操作に便利なショートカットを提供します。 たとえば、アプリケーションが 2 つの異なるバッファー セットからデータを挿入するとします。 バッファーの最初のセットを使用するには、繰り返し**SQLBindParameter**を呼び出して **、INSERT**ステートメントのパラメーターにバインドし、ステートメントを実行します。 2 番目のバッファ セットを使用するには、このプロセスを繰り返します。 あるいは、ある記述子のバッファーの最初のセットと、別の記述子のバッファーの 2 番目のセットへのバインディングをセットアップすることもできます。 バインディングのセットを切り替えるには、アプリケーションは**SQLSetStmtAttr**を呼び出し、正しい記述子をステートメントに APD として関連付けます。  
  
 記述子の詳細については、記述子[のタイプを](../../../odbc/reference/develop-app/types-of-descriptors.md)参照してください。
