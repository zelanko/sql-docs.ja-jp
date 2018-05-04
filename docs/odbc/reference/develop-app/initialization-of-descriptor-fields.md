---
title: 記述子フィールドの初期化を |Microsoft ドキュメント
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
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1875f69e3ba26a331b5042ebcdaaa803559f772a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="initialization-of-descriptor-fields"></a>記述子フィールドの初期化
アプリケーション行記述子が割り当てられると、そのフィールドが表示される初期値で指定されている[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。 SQL_DESC_TYPE フィールドの初期値は、SQL_DEFAULT です。 これは、アプリケーションに提示するためのデータベース データの標準的な処理方法を提供します。 アプリケーションは、記述子レコードのフィールドを設定して、データのさまざまな処理方法を指定することがあります。  
  
 記述子のヘッダーに SQL_DESC_ARRAY_SIZE の初期値は 1 です。 アプリケーションでは、複数行のフェッチを有効にするには、このフィールドを変更できます。  
  
 IRD のフィールドについて、既定値の概念が正しくありません。 アプリケーションは、関連付けられている準備または実行されたステートメントがある場合にのみ、IRD のフィールドへのアクセスを取得できます。  
  
 ドライバーが自動的に設定されて、IPD 後にのみ、IPD の特定のフィールドが定義されます。 いない場合は、定義はありません。 これらのフィールドは SQL_DESC_CASE_SENSITIVE、SQL_DESC_FIXED_PREC_SCALE、SQL_DESC_TYPE_NAME、SQL_DESC_UNSIGNED、および SQL_DESC_LOCAL_TYPE_NAME です。
