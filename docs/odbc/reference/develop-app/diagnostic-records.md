---
title: 診断レコード |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6395d87e5691dc33b5a08267ef83c459f94c0d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909317"
---
# <a name="diagnostic-records"></a>診断レコード
各環境に関連付けられた、接続、ステートメント、および記述子ハンドルは*診断レコード*です。 これらのレコードと呼ばれる特定のハンドルを使用する最後の関数に関する診断情報が含まれています。 ハンドルを使用して別の関数が呼び出されたときにのみ、レコードが置き換えられます。 任意の時点で格納できる診断レコードの数に制限はありません。  
  
 診断レコードの 2 種類があります。*ヘッダー レコード*と 0 個以上*状態レコード*です。 ヘッダー レコードはレコード 0 です。状態レコードは、レコード 1 以降。 診断レコードのヘッダー レコードと状態レコードが異なりますが、個別のフィールドの数で構成されます。 さらに、ODBC コンポーネントでは、独自の診断レコードのフィールドを定義できます。  
  
 構造体です。 を実際にするためには必要はありませんが、診断レコードは、構造体として考えることができます、ドライバーが、診断情報を格納する方法と、ドライバー固有です。  
  
 診断レコードのフィールドが取得されます**SQLGetDiagField**です。 1 回の呼び出しで取得できる、SQLSTATE、ネイティブ エラー番号と状態レコードの診断メッセージ フィールド**SQLGetDiagRec**です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ヘッダー レコード](../../../odbc/reference/develop-app/header-record.md)  
  
-   [状態レコード](../../../odbc/reference/develop-app/status-records.md)
