---
title: 間隔のエスケープ シーケンス |Microsoft ドキュメント
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
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e3a475170fed349a5bf85eb4f23bb93fe4ae804
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="interval-escape-sequences"></a>間隔のエスケープ シーケンス
ODBC では、間隔のリテラルのエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
 {*間隔リテラル*}  
  
 BNF 構文の*間隔リテラル*を参照してください、[間隔リテラル構文](../../../odbc/reference/appendixes/interval-literal-syntax.md)この付録の後半の「します。  
  
 間隔のリテラルのエスケープ シーケンスには、interval データ型が、データ ソースによってサポートされている場合はサポートされています。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**をこれらのデータ型がサポートされているかどうかを判断します。
