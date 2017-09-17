---
title: "同時実行の種類 |Microsoft ドキュメント"
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
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 737fadc881109457051cf30bfce9b493bd164f1c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="concurrency-types"></a>同時実行の種類
カーソルの削減の同時実行の問題を解決するには、ODBC は、次の 4 つのさまざまな種類のカーソルの同時実行を公開します。  
  
-   **読み取り専用**カーソルことができますデータの読み取りができないデータ更新または削除します。 これは、既定の同時実行の種類です。 DBMS には、Repeatable Read と Serializable 分離レベルを適用する行をロックが、書き込みロックではなく読み取りロックを使用できます。 これは、結果、他のトランザクションでは、データを読み取ることができますには、少なくともため同時実行性。  
  
-   **ロック**カーソルは、最低限のロックを更新したり、結果セット内の行を削除したりかどうかを確認するために必要なを使用します。 これは、通常、Repeatable Read および Serializable トランザクション分離レベルで特に、非常に低い同時実行レベルで発生します。  
  
-   **行のバージョンを使用してオプティミスティック同時実行と値を使用してオプティミスティック同時実行**カーソルはオプティミスティック同時実行制御を使用: 更新または最後の読み取り以降に変更されていない場合にのみ、行を削除します。 変更を検出するには、行のバージョンまたは値を比較します。 カーソルは更新または行を削除するようになりますが、同時実行性がロックを使用する場合より高い保証はありません。 詳細については、次のセクションを参照してください。[オプティミスティック同時実行制御](../../../odbc/reference/develop-app/optimistic-concurrency.md)です。  
  
 アプリケーションでは、SQL_ATTR_CONCURRENCY ステートメント属性で使用するカーソルが同時実行の種類を指定します。 サポートされる種類を決定するには、呼び出し**SQLGetInfo** SQL_SCROLL_CONCURRENCY オプションを使用します。
