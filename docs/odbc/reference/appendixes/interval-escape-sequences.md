---
title: "間隔のエスケープ シーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9be0ccc925003985c9c680d3107029a929403643
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="interval-escape-sequences"></a>間隔のエスケープ シーケンス
ODBC では、間隔のリテラルのエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
 {*間隔リテラル*}  
  
 BNF 構文の*間隔リテラル*を参照してください、[間隔リテラル構文](../../../odbc/reference/appendixes/interval-literal-syntax.md)この付録の後半の「します。  
  
 間隔のリテラルのエスケープ シーケンスには、interval データ型が、データ ソースによってサポートされている場合はサポートされています。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**をこれらのデータ型がサポートされているかどうかを判断します。
