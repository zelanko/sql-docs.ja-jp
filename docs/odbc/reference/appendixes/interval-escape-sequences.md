---
title: インターバルエスケープシーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fe7f6941e9ec9fba8b6698faaa18a678732dd6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304957"
---
# <a name="interval-escape-sequences"></a>Interval のエスケープ シーケンス
ODBC では、間隔リテラルにエスケープ シーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
 {*間隔リテラル*}  
  
 *間隔リテラル*の BNF 構文については、この付録の後半にある[「間隔リテラル構文」](../../../odbc/reference/appendixes/interval-literal-syntax.md)を参照してください。  
  
 間隔リテラルのエスケープ シーケンスは、間隔データ型がデータ ソースでサポートされている場合にサポートされます。 アプリケーションは、これらのデータ型がサポートされているかどうかを判断するのに**は SQLGetTypeInfo**を呼び出す必要があります。
