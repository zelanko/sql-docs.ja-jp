---
title: グレゴリオ暦の制約 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f88842c7426e17af1fdc0533b8b97e2c559de237
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284762"
---
# <a name="constraints-of-the-gregorian-calendar"></a>グレゴリオ暦カレンダーの制限
日付と日時のデータ型、および間隔データ型の末尾のフィールドは、グレゴリオ暦の制約に準拠する必要があります。 これらの制約は次のとおりです。  
  
-   月フィールドの値は、1 から 12 までの範囲で指定する必要があります。  
  
-   日フィールドの値は、1 から月の日数までの範囲内にする必要があります。 月の日数は、年と月のフィールドの値から決定され、28、29、30、または 31 にすることができます。 (月の日数は、うるう年かどうかによっても異なります。  
  
-   時間フィールドの値は 0 ~ 23 の範囲で指定する必要があります。  
  
-   分フィールドの値は 0 から 59 の範囲で指定する必要があります。  
  
-   間隔データ型の末尾の秒フィールドの場合、秒フィールドの値は 0 から 59.9(*n*)*n*の範囲でなければなりません 。  
  
-   datetime データ型の末尾の秒フィールドの場合、秒フィールドの値は 0 ~ 61.9(*n*)*n*の範囲で指定する必要があります。 *n* (秒の範囲では、2 回のうるう秒がサイドリアルタイムの同期を維持できます)。
