---
title: パラメーターのデータ型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6c2a73aec119b7572cad93dedb2994235329cb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826032"
---
# <a name="parameter-data-types"></a>パラメーターのデータ型
各パラメーターが指定されている場合でも**SQLBindParameter**は、SQL データ型を SQL ステートメントのパラメーターを使用して定義されていない組み込みデータ型であります。 そのため、パラメーター マーカーはステートメントのもう 1 つのオペランドからそのデータ型を推論することができる場合にのみ、SQL ステートメントに含めることができます。 でなどの算術式でしょうか。 + COLUMN1、パラメーターのデータ型は、列 1 で表される名前付きの列のデータ型から推論することができます。 データ型を特定できない場合、アプリケーションでパラメーター マーカーを使用することはできません。  
  
 次の表では、SQL 92 に従って、パラメーターのいくつかの種類のデータ型を決定する方法について説明します。 他の SQL 句を使用する場合、パラメーターの型の推論のより包括的な仕様は、SQL 92 仕様を参照してください。  
  
|パラメーターの場所|データ型と見なされます|  
|---------------------------|-----------------------|  
|二項演算または比較演算子の 1 つのオペランド|もう一方のオペランドと同じ|  
|最初のオペランドを**BETWEEN**句|2 番目のオペランドと同じ|  
|2 番目または 3 番目のオペランドを**BETWEEN**句|最初のオペランドと同じ|  
|使用される式**IN**|最初の値またはサブクエリの結果列と同じ|  
|使用される値**IN**|式または式でパラメーター マーカーがある場合は、最初の値と同じ|  
|使用されるパターン値**など**|VARCHAR|  
|使用される更新プログラム値**更新**|[更新] 列と同じ|
