---
title: Interval データ型の長さ |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284322"
---
# <a name="interval-data-type-length"></a>Interval データ型の長さ
次の規則は、期間データ型の長さを文字数で決定するために使用されます。 長さは文字数で表現されます。 バイト数は、文字セットによって異なります。 長さには、次の値が一緒に追加されます。  
  
-   先頭のフィールドではない、間隔内のすべてのフィールドに対して2文字。  
  
-   先頭のフィールドで、明示的または暗黙的な有効桁数である文字の数。 先頭の有効桁数が指定されていない場合、既定値は2です。  
  
-   フィールド間の区切り記号として1文字。  
  
-   1に加えて、秒または暗黙の秒の有効桁数。 秒の有効桁数が指定されていない場合、既定値は6です。  
  
 各 interval データ型の特定の列長の値は、[列のサイズ](../../../odbc/reference/appendixes/column-size.md)に含まれています。
