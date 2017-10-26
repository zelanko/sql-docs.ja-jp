---
title: "記述子フィールドの値を取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f86dd2e2cb625da359c677fedd297b510fee8593
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-the-values-in-descriptor-fields"></a>記述子フィールドの値を取得します。
アプリケーションが呼び出すことができます**SQLGetDescField**を記述子レコードの 1 つのフィールドを取得します。 **Sqlgetdescfield による**ODBC では、定義されたすべての記述子フィールドとドライバーの定義済みのフィールドも、アプリケーションにアクセスします。  
  
 **SQLGetDescRec**列またはパラメーターのデータのストレージとデータ型に影響する複数の記述子フィールドの設定を取得すると呼ばれることができます。

