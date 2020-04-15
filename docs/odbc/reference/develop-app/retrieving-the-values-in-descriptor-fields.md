---
title: 記述子フィールドの値を取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 43467d19f3f2e576efa0402c4ba513e23da59390
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304323"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>記述子フィールドの値の取得
アプリケーションは、記述子レコードの単一のフィールドを取得する**SQLGetDescField**を呼び出すことができます。 **SQLGetDescField**は、ODBC で定義されているすべての記述子フィールド、およびドライバー定義フィールドにもアプリケーションアクセスを提供します。  
  
 **SQLGetDescRec**を呼び出して、データ型と列またはパラメーター データの格納に影響を与える複数の記述子フィールドの設定を取得できます。
