---
title: 記述子フィールドの初期化 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300122"
---
# <a name="initialization-of-descriptor-fields"></a>記述子フィールドの初期化
アプリケーション行記述子が割り当てられると、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)に示された初期値が、そのフィールドに受け取られます。 SQL_DESC_TYPE フィールドの初期値はSQL_DEFAULT。 これにより、アプリケーションに表示するデータベース データの標準的な処理が提供されます。 アプリケーションは、記述子レコードのフィールドを設定することにより、データの異なる処理を指定できます。  
  
 記述子ヘッダーのSQL_DESC_ARRAY_SIZEの初期値は 1 です。 アプリケーションは、このフィールドを変更して、複数行のフェッチを有効にすることができます。  
  
 IRD のフィールドに対して、デフォルト値の概念が有効ではありません。 アプリケーションは、IRD のフィールドにアクセスできるのは、準備済みまたは実行済みのステートメントが関連付けられている場合のみです。  
  
 IPD の特定のフィールドは、ドライバーによって IPD が自動的に設定された後にのみ定義されます。 定義されていない場合、それらは未定義です。 これらのフィールドは、SQL_DESC_CASE_SENSITIVE、SQL_DESC_FIXED_PREC_SCALE、SQL_DESC_TYPE_NAME、SQL_DESC_UNSIGNED、およびSQL_DESC_LOCAL_TYPE_NAMEです。
