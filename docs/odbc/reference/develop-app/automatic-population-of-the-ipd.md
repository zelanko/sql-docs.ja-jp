---
title: IPD の自動作成 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1998ea1992ee7f14d87d01e348d955b017166088
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285072"
---
# <a name="automatic-population-of-the-ipd"></a>IPD の自動作成
一部のドライバーは、パラメーター化クエリが準備された後に IPD のフィールドを設定できます。 記述子フィールドには、データ・タイプ、精度、位取り、およびその他の特性など、パラメーターに関する情報が自動的に入力されます。 これは **、SQLDescribe パラム**をサポートすることと同じです。 この情報は、アプリケーションが認識していないパラメーターを使用してアドホック クエリを実行する場合など、アプリケーションを検出する他の方法がない場合に、特に役立ちます。  
  
 アプリケーションは、ドライバーがSQL_ATTR_AUTO_IPDの*属性*を使用して**SQLGetConnectAttr**を呼び出すことによって、自動作成をサポートするかどうかを決定します。 SQL_TRUEが返された場合、ドライバーはそれをサポートし、アプリケーションは、SQL_ATTR_ENABLE_AUTO_IPDステートメント属性をSQL_TRUEに設定することで、それを有効にすることができます。  
  
 自動作成がサポートされ、有効になっている場合、パラメーター マーカーを含む SQL ステートメントが**SQLPrepare**の呼び出しによって準備された後、ドライバーは IPD のフィールドにデータを入力します。 アプリケーションは **、SQLGetDescField**または**SQLGetDescRec**、または**SQLDescribeParam**を呼び出すことによって、この情報を取得できます。 アプリケーションは、この情報を使用して、パラメーターに最も適切なアプリケーション・バッファーをバインドしたり、そのパラメーターにデータ変換を指定したりできます。  
  
 IPD の自動作成により、パフォーマンスが低下する可能性があります。 アプリケーションは、SQL_ATTR_ENABLE_AUTO_IPDステートメント属性をSQL_FALSE (デフォルト値) にリセットすることで、この属性をオフにすることができます。
