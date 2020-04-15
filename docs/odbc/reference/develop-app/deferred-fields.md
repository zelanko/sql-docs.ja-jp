---
title: 繰延フィールド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 094aba353e10ed568e1959b1d655109296507dee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305973"
---
# <a name="deferred-fields"></a>遅延フィールド
*遅延フィールド*の値は、設定時には使用されませんが、ドライバーは、遅延効果の変数のアドレスを保存します。 アプリケーション パラメーター記述子の場合、ドライバーは**SQLExecDirect**または**SQLExecute**の呼び出し時に変数の内容を使用します。 アプリケーション行記述子の場合、ドライバーはフェッチ時に変数の内容を使用します。  
  
 以下は、遅延フィールドです。  
  
-   記述子レコードのSQL_DESC_DATA_PTRフィールドとSQL_DESC_INDICATOR_PTRフィールド。  
  
-   アプリケーション記述子レコードのSQL_DESC_OCTET_LENGTH_PTRフィールド。  
  
-   複数行フェッチの場合、記述子ヘッダーのSQL_DESC_ARRAY_STATUS_PTRフィールドとSQL_DESC_ROWS_PROCESSED_PTRフィールド。  
  
 記述子が割り振られている場合、各記述子レコードの据え置きフィールドには、最初に NULL 値が入ります。 NULL 値の意味は次のとおりです。  
  
-   SQL_DESC_ARRAY_STATUS_PTRに null 値が設定されている場合、複数行フェッチは、行ごとの診断情報のこのコンポーネントを返しません。  
  
-   SQL_DESC_DATA_PTRに null 値が設定されている場合、レコードはバインド解除されます。  
  
-   ARD のSQL_DESC_OCTET_LENGTH_PTRフィールドに null 値がある場合、ドライバーはその列の長さ情報を返しません。  
  
-   APD のSQL_DESC_OCTET_LENGTH_PTRフィールドに null 値があり、パラメーターが文字列である場合、ドライバーは文字列が null で終わるものと見なします。 出力動的パラメーターの場合、このフィールドに null 値を指定すると、ドライバーが長さ情報を返すことを防ぎます。 SQL_DESC_TYPEフィールドが文字ストリング・パラメーターを示さない場合、SQL_DESC_OCTET_LENGTH_PTRフィールドは無視されます。  
  
 アプリケーションは、遅延フィールドに使用される変数を、フィールドに関連付けてから、ドライバーが読み取りまたは書き込みを行うまでの間に、その変数を解放または破棄してはなりません。
