---
title: 記述子ハンドル |Microsoft ドキュメント
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
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8af53ab1826f2e7a6ee634ec70c4badb20ef6c96
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="descriptor-handles"></a>記述子ハンドル
A*記述子*SQL ステートメントのパラメーターまたは結果セットの列を説明するメタデータのコレクションは、アプリケーションまたはドライバーが表示される (とも呼ばれる、*実装*)。 このため、記述子では 4 つのロールのいずれかを入力できます。  
  
-   **アプリケーション パラメーター記述子 (APD)。** そのアドレス、長さ、および C データ型など、SQL ステートメントのパラメーターにバインドされているアプリケーション バッファーについての情報が含まれています。  
  
-   **実装パラメーター記述子 (IPD)。** SQL データ型、長さ、null 値許容属性など、SQL ステートメントのパラメーターに関する情報が含まれています。  
  
-   **アプリケーション行記述子 (ARD)。** そのアドレス、長さ、および C データ型などの結果セット内の列にバインドされているアプリケーション バッファーについての情報が含まれています。  
  
-   **実装行記述子 (IRD)。** SQL データ型、長さ、null 値許容属性などの結果セット内の列に関する情報が含まれています。  
  
 (1 つそれぞれの役割を担う) 4 つの記述子は、ステートメントが割り当てられているときに自動的に割り当てられます。 これらと呼ばれます*記述子を自動的に割り当てられた*とそのステートメントに関連付けられた常にします。 アプリケーションと記述子を割り当てることができますも**SQLAllocHandle**です。 これらと呼ばれます*記述子を明示的に割り当てられた*です。 接続上に割り当てられた、これらのステートメントで APD または ARD の役割を実行するには、その接続で 1 つまたは複数のステートメントを関連付けることができます。  
  
 ODBC でのほとんどの操作は、アプリケーションによって記述子の明示的な使用せずに実行できます。 ただし、記述子は、いくつかの操作の便利なショートカットを提供します。 たとえば、アプリケーションがバッファーの 2 つの異なるセットからデータを挿入しようとします。 バッファーの最初のセットを使用するのには繰り返し呼び出すことが**SQLBindParameter**のパラメーターにバインドして、**挿入**ステートメントと、ステートメントを実行します。 バッファーの 2 番目のセットを使用するのには、このプロセスを繰り返しますが。 または、バインディング記述子が 1 つのバッファーの最初のセットにし、別の記述子にバッファーの 2 番目のセットをそのセットアップでした。 バインドのセットの間には、アプリケーションは単に呼び出します**SQLSetStmtAttr**し APD としてステートメントを使用して、正しい記述子を関連付けます。  
  
 記述子の詳細については、次を参照してください。[型の記述子](../../../odbc/reference/develop-app/types-of-descriptors.md)です。
