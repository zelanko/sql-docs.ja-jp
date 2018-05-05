---
title: フィールドを遅延 |Microsoft ドキュメント
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
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc2020dc36ce031391194695e40308431c0f06d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="deferred-fields"></a>遅延のフィールド
値*フィールドを遅延*設定されているが、ドライバーは、遅延の影響用の変数のアドレスを保存する場合は使用しません。 ドライバー、アプリケーション パラメーター記述子への呼び出し時に、変数の内容を使用して**SQLExecDirect**または**SQLExecute**です。 アプリケーション行記述子では、ドライバーは、フェッチ時に、変数の内容を使用します。  
  
 遅延のフィールドを次に示します。  
  
-   記述子レコードの SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR フィールドです。  
  
-   アプリケーションの記述子レコードの SQL_DESC_OCTET_LENGTH_PTR フィールドです。  
  
-   複数行のフェッチの場合、記述子のヘッダー フィールドの SQL_DESC_ARRAY_STATUS_PTR と SQL_DESC_ROWS_PROCESSED_PTR フィールドです。  
  
 記述子が割り当てられる各記述子レコードのフィールドの遅延は最初に null 値を保持します。 Null 値の意味は次のとおりです。  
  
-   SQL_DESC_ARRAY_STATUS_PTR に null 値がある場合は、このコンポーネントの行ごとの診断情報を返す複数行のフェッチは失敗します。  
  
-   SQL_DESC_DATA_PTR が null の値を持つ場合、レコードはバインドできません。  
  
-   ARD の SQL_DESC_OCTET_LENGTH_PTR フィールドに null 値がある場合、ドライバーはその列の長さの情報を返しません。  
  
-   APD の SQL_DESC_OCTET_LENGTH_PTR フィールドに null 値があり、ユーザーが、パラメーターは、文字の文字列は、ドライバーは、文字列が null で終わるであると仮定します。 出力の動的パラメーターに対してこのフィールドに null 値には、長さの情報を返すからドライバーができなくなります。 (SQL_DESC_TYPE フィールドが文字の文字列パラメーターを示していない場合、SQL_DESC_OCTET_LENGTH_PTR フィールドは無視されます。)  
  
 アプリケーションは、割り当てを解除できませんまたはフィールドとそれらを関連付けます時間と、ドライバーの読み取りまたは書き込みに時間の間の遅延のフィールドに使用される変数を破棄します。
