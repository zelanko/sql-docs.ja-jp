---
title: "構成のグレゴリオ暦カレンダーの制約 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1b149b1e9df8338b5502d57e6e7eb355b66bcc3f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="constraints-of-the-gregorian-calendar"></a>構成のグレゴリオ暦カレンダーの制約
日付、および日時のデータ型、および interval データ型の後続のフィールドは、グレゴリオ暦の制約に従う必要があります。 これらの制約は次のとおりです。  
  
-   月のフィールドの値は、1 から 12 の間でなければなりません。  
  
-   日フィールドの値は、1 月の日数の数までの範囲内でなければなりません。 月の日数は、年と月のフィールドの値からは決定され、28、29、30、または 31 を指定できます。 (月の日数を指定できますも異なります閏年であるかどうか。)  
  
-   時間のフィールドの値は、0 ~ 23 の範囲の間にする必要があります。  
  
-   分単位のフィールドの値は、0 ~ 59、間にする必要があります。  
  
-   Interval データ型の後続の秒フィールドの秒フィールドの値が 0 ~ 59.9 でなければなりません (*n*), inclusive、場所 *n* の数字の数が、秒の小数部の有効桁数です。  
  
-   Datetime データ型の後続の秒フィールドの秒フィールドの値は 0 ~ 61.9 の間にする必要があります (*n*)、包含的な場所 *n*  「9」の数を指定します値と数字 *n* 秒の小数部の有効桁数です。 (秒の範囲は、sidereal 時間の同期を維持するために最大で 2 つのうるう秒を許可する)。

