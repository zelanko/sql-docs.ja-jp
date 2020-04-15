---
title: 診断記録 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b564f2837bc76e04011170e191d00c08d10c119d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305183"
---
# <a name="diagnostic-records"></a>診断レコード
各環境、接続、ステートメント、および記述子ハンドルに関連付けられている*診断レコード*。 これらのレコードには、特定のハンドルを使用した最後の関数に関する診断情報が含まれています。 レコードは、そのハンドルを使用して別の関数が呼び出された場合にのみ置き換えられます。 一度に保存できる診断レコードの数に制限はありません。  
  
 診断レコードには、*ヘッダー レコード*と 0 個以上の*状態レコード*の 2 種類があります。 ヘッダー レコードはレコード 0 です。状態レコードはレコード 1 以上です。 診断レコードは、ヘッダー レコードと状態レコードで異なる、いくつかの個別のフィールドで構成されます。 さらに、ODBC コンポーネントは、独自の診断レコード フィールドを定義できます。  
  
 診断レコードは構造と考えることができますが、実際に構造を使用する必要はありません。ドライバが診断情報を格納する方法は、ドライバ固有です。  
  
 診断レコードのフィールドは、 **SQLGetDiagField**で取得されます。 SQLSTATE、ネイティブ・エラー番号、および状況レコードの診断メッセージ・フィールドは、 **SQLGetDiagRec**を使用した単一の呼び出しで検索できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ヘッダー レコード](../../../odbc/reference/develop-app/header-record.md)  
  
-   [状態レコード](../../../odbc/reference/develop-app/status-records.md)
