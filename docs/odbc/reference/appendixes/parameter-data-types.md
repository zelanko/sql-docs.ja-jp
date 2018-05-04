---
title: パラメーターのデータ型 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a43fdab2fd7ffeaf409bde41c06386fad23d3c3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-data-types"></a>パラメーターのデータ型
各パラメーターが指定された場合でも**SQLBindParameter**は、SQL データ型を SQL ステートメント内のパラメーターを使用して定義されていない組み込みデータ型であります。 そのため、パラメーター マーカーは、ステートメント内の別のオペランドからのデータ型を推論できる場合にのみ、SQL ステートメントに含めることができます。 たとえばなどの算術式でしますか。 + COLUMN1、パラメーターのデータ型は、COLUMN1 によって表される名前付きの列のデータ型から推論することができます。 データ型を特定できない場合、アプリケーションでパラメーター マーカーを使用することはできません。  
  
 次の表では、いくつかの種類、sql-92 に従って、パラメーターのデータ型を決定する方法について説明します。 他の SQL 句を使用する場合は、パラメーターの型を推論するときより包括的な仕様では、SQL 92 仕様を参照してください。  
  
|パラメーターの位置|データ型と見なされます|  
|---------------------------|-----------------------|  
|二項演算または比較演算子の 1 つのオペランド|もう一方のオペランドと同じ|  
|最初のオペランドで、 **BETWEEN**句|2 番目のオペランドと同じ|  
|2 番目または 3 番目のオペランド、 **BETWEEN**句|最初のオペランドと同じ|  
|使用される式**IN**|最初の値またはサブクエリの結果列と同じ|  
|使用される値**IN**|式または式でパラメーター マーカーがある場合は、最初の値と同じ|  
|使用されるパターン値**など**|VARCHAR|  
|使用される、更新値**更新**|[更新] 列と同じ|
