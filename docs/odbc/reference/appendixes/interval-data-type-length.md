---
title: "間隔のデータ型の長さ |Microsoft ドキュメント"
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
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e642685b670fa872c1a34d2d10fed815e5a6fa7e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="interval-data-type-length"></a>Interval データ型の長さ
次の規則は、間隔でデータ型の文字の長さを決定に使用されます。 長さは、文字数で表されます。 バイト数は、文字セットによって異なります。 長さには、次の値一緒に追加にはが含まれています。  
  
-   すべてのフィールドの先頭のフィールドではなく、間隔で 2 つの文字です。  
  
-   先頭のフィールドには、明示的または暗黙的なの文字数は、有効桁数を先頭します。 先頭の有効桁数が指定されていない場合、既定値は 2 です。  
  
-   フィールド間の区切り記号の文字を 1 つ。  
  
-   1 を加えた明示または黙示を問わず秒の有効桁数です。 秒の有効桁数が指定されていない場合、既定値は 6 です。  
  
 特定の列の各データ型の間隔の長さの値が含まれている[列サイズ](../../../odbc/reference/appendixes/column-size.md)です。
