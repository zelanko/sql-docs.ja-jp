---
title: パラメータの説明 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f4d9284294707da0a469bf75ff9812ad5f7855bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305943"
---
# <a name="describing-parameters"></a>パラメーターの記述
**SQLBindParameter には**、SQL 型、有効桁数、およびスケールのパラメーターを記述する引数があります。 ドライバーは、この情報、つまり*メタデータ*を使用して、パラメーター値をデータ ソースに必要な型に変換します。 一見すると、ドライバーは、アプリケーションよりもパラメーターのメタデータを知っているより良い位置にあるように見えるかもしれません。結局のところ、ドライバーは結果セット列のメタデータを簡単に検出できます。 結局のところ、これは当てはまりません。 まず、ほとんどのデータ ソースは、ドライバーがパラメーター メタデータを検出する方法を提供していません。 第二に、ほとんどのアプリケーションは、すでにメタデータを知っています。  
  
 アプリケーションで SQL ステートメントがハードコーディングされている場合、アプリケーション作成者は、各パラメーターのタイプを既に認識しています。 実行時にアプリケーションによって SQL ステートメントが構築される場合、アプリケーションはステートメントのビルド時にメタデータを判別できます。 たとえば、アプリケーションが句を作成する場合  
  
```  
WHERE OrderID = ?  
```  
  
 この場合、ORDERID 列の**SQLColumns**を呼び出すことができます。  
  
 アプリケーションがパラメーター メタデータを簡単に判断できない状況は、ユーザーがパラメーター化されたステートメントを入力したときだけです。 この場合、アプリケーションは**SQLPrepare**を呼び出してステートメントを準備し **、SQLNumParams を呼**び出してパラメーターの数を決定し、各パラメーターを記述する**SQLDescribeParam**を呼び出します。 ただし、前述のように、ほとんどのデータ ソースは、ドライバーがパラメーター のメタデータを検出する方法を提供**しません。**
