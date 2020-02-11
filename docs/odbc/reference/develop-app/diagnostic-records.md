---
title: 診断レコード |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 90133b4a18876c52b9b6b6bffbe4c8c02c953e07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039879"
---
# <a name="diagnostic-records"></a>診断レコード
各環境、接続、ステートメント、記述子ハンドルに関連付けられている*診断レコード*です。 これらのレコードには、特定のハンドルを使用した、最後に呼び出された関数に関する診断情報が含まれています。 レコードは、そのハンドルを使用して別の関数が呼び出された場合にのみ置換されます。 一度に保存できる診断レコードの数に制限はありません。  
  
 診断レコードには、*ヘッダーレコード*と0個以上の*状態レコード*の2種類があります。 ヘッダーレコードはレコード0です。状態レコードは、1以上のレコードです。 診断レコードは、ヘッダーレコードと状態レコードで異なるさまざまなフィールドで構成されます。 さらに、ODBC コンポーネントでは、独自の診断レコードフィールドを定義できます。  
  
 診断レコードは構造として考えることができますが、実際には構造体である必要はありません。ドライバーが診断情報を格納する方法は、ドライバーによって異なります。  
  
 診断レコードのフィールドは、 **SQLGetDiagField**を使用して取得されます。 ステータスレコードの SQLSTATE、ネイティブエラー番号、および診断メッセージフィールドは、 **SQLGetDiagRec**を使用して1回の呼び出しで取得できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ヘッダー レコード](../../../odbc/reference/develop-app/header-record.md)  
  
-   [状態レコード](../../../odbc/reference/develop-app/status-records.md)
