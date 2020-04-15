---
title: 間隔データ型の長さ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68bb4daa47cb58d5a0ff7b680a2d2154fb14b345
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284322"
---
# <a name="interval-data-type-length"></a>Interval データ型の長さ
次の規則は、間隔データ型の長さを文字で決定するために使用されます。 長さは文字数で表されます。 バイト数は文字セットによって異なります。 長さには、次の値が加算されます。  
  
-   間隔の先頭フィールドではない各フィールドに 2 文字。  
  
-   先行フィールドの場合、明示的または暗黙的な先行精度である文字数。 先行する精度が指定されていない場合、デフォルト値は 2 です。  
  
-   フィールド間の区切り記号の 1 文字。  
  
-   1 + 明示的または暗黙的な秒精度。 秒精度が指定されていない場合、デフォルト値は 6 です。  
  
 各間隔データ型の特定の列長の値は、 [[ 列サイズ ]](../../../odbc/reference/appendixes/column-size.md)に含まれています。
