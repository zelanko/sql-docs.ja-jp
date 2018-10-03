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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16d0590d3297b52891bf399822ce984674022583
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47808932"
---
# <a name="interval-data-type-length"></a>Interval データ型の長さ
次の規則は、文字間隔のデータ型の長さを決定に使用されます。 長さは、文字数で表されます。 バイト数は、文字セットに依存します。 長さには、次の値一緒に追加にはが含まれています。  
  
-   2 つの文字の先頭のフィールドではなく、間隔のすべてのフィールド。  
  
-   先頭のフィールドでは、明示または暗黙の先頭有効桁数は、文字数。 先頭の有効桁数が指定されていない場合、既定値は 2 です。  
  
-   1 つのフィールド間の区切り記号文字。  
  
-   1 を加えたまたは黙示を問わず秒の有効桁数。 秒の有効桁数が指定されていない場合、既定値は 6 です。  
  
 間隔のデータ型ごとに特定の列の長さの値に含まれる[列サイズ](../../../odbc/reference/appendixes/column-size.md)します。
