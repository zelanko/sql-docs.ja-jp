---
title: 記述子フィールドの値を取得する |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b9b00624f9d327e4c561c2d7272e7459e3ed176
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>記述子フィールドの値を取得します。
アプリケーションが呼び出すことができます**SQLGetDescField**を記述子レコードの 1 つのフィールドを取得します。 **Sqlgetdescfield による**ODBC では、定義されたすべての記述子フィールドとドライバーの定義済みのフィールドも、アプリケーションにアクセスします。  
  
 **SQLGetDescRec**列またはパラメーターのデータのストレージとデータ型に影響する複数の記述子フィールドの設定を取得すると呼ばれることができます。
