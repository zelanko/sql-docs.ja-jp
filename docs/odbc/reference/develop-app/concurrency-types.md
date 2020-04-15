---
title: 同時実行の種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 642301d09c5aa189276db534e58aca0c5e00e3ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299102"
---
# <a name="concurrency-types"></a>コンカレンシーの種類
カーソルの同時実行性が減少するという問題を解決するために、ODBC は次の 4 種類のカーソル同時実行性を公開します。  
  
-   **読み取り専用**カーソルはデータを読み取ることができますが、データを更新または削除することはできません。 これは、既定の同時実行の種類です。 DBMS は、繰り返し読み取り可能な分離レベルとシリアライズ可能分離レベルを適用するために行をロックする場合がありますが、書き込みロックの代わりに読み取りロックを使用できます。 他のトランザクションが少なくともデータを読み取ることができるため、この結果、同時実行性が高くなります。  
  
-   **ロック**カーソルは、結果セット内の行を更新または削除するために必要な最下位レベルのロックを使用します。 通常、この結果として、特に反復可能読み取りおよび直列化可能トランザクション分離レベルでは、同時実行レベルが非常に低くなります。  
  
-   **行バージョンを使用したオプティミスティック同時実行制御と値を使用したオプティミスティック同時実行制御**カーソルはオプティミスティック同時実行制御を使用します: 最後に読み取られた後に変更されていない行のみを更新または削除します。 変更を検出するために、行のバージョンまたは値を比較します。 カーソルが行を更新または削除できる保証はありませんが、同時実行性はロックを使用する場合よりもはるかに高くなります。 詳細については、次のセクション「[オプティミスティック同時実行制御](../../../odbc/reference/develop-app/optimistic-concurrency.md)」を参照してください。  
  
 アプリケーションは、SQL_ATTR_CONCURRENCY ステートメント属性で使用するカーソルの同時実行制御の種類を指定します。 サポートされている型を確認するために、SQL_SCROLL_CONCURRENCY オプションを指定して**SQLGetInfo**を呼び出します。
