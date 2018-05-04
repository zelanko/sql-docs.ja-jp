---
title: 同時実行の種類 |Microsoft ドキュメント
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
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e65be0d19d1baa6f9cad2b9b386e032d17a0c5a7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="concurrency-types"></a>同時実行の種類
カーソルの削減の同時実行の問題を解決するには、ODBC は、次の 4 つのさまざまな種類のカーソルの同時実行を公開します。  
  
-   **読み取り専用**カーソルことができますデータの読み取りができないデータ更新または削除します。 これは、既定の同時実行の種類です。 DBMS には、Repeatable Read と Serializable 分離レベルを適用する行をロックが、書き込みロックではなく読み取りロックを使用できます。 これは、結果、他のトランザクションでは、データを読み取ることができますには、少なくともため同時実行性。  
  
-   **ロック**カーソルは、最低限のロックを更新したり、結果セット内の行を削除したりかどうかを確認するために必要なを使用します。 これは、通常、Repeatable Read および Serializable トランザクション分離レベルで特に、非常に低い同時実行レベルで発生します。  
  
-   **行のバージョンを使用してオプティミスティック同時実行と値を使用してオプティミスティック同時実行**カーソルはオプティミスティック同時実行制御を使用: 更新または最後の読み取り以降に変更されていない場合にのみ、行を削除します。 変更を検出するには、行のバージョンまたは値を比較します。 カーソルは更新または行を削除するようになりますが、同時実行性がロックを使用する場合より高い保証はありません。 詳細については、次のセクションを参照してください。[オプティミスティック同時実行制御](../../../odbc/reference/develop-app/optimistic-concurrency.md)です。  
  
 アプリケーションでは、SQL_ATTR_CONCURRENCY ステートメント属性で使用するカーソルが同時実行の種類を指定します。 サポートされる種類を決定するには、呼び出し**SQLGetInfo** SQL_SCROLL_CONCURRENCY オプションを使用します。
