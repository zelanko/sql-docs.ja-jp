---
title: "間隔のエスケープ シーケンス |Microsoft ドキュメント"
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
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8088c0cb3f85b375423f636d2def8c08c04bbe28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="interval-escape-sequences"></a>間隔のエスケープ シーケンス
ODBC では、間隔のリテラルのエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
 {*間隔リテラル*}  
  
 BNF 構文の*間隔リテラル*を参照してください、[間隔リテラル構文](../../../odbc/reference/appendixes/interval-literal-syntax.md)この付録の後半の「します。  
  
 間隔のリテラルのエスケープ シーケンスには、interval データ型が、データ ソースによってサポートされている場合はサポートされています。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**をこれらのデータ型がサポートされているかどうかを判断します。

