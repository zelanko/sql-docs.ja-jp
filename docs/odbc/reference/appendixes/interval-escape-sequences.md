---
title: 間隔エスケープシーケンス |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c674ee8838273af9bf4ed91ddcead7e1768fb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041639"
---
# <a name="interval-escape-sequences"></a>Interval のエスケープ シーケンス
ODBC では、間隔リテラルにエスケープシーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
 {*interval-リテラル*}  
  
 *Interval リテラル*の BNF 構文については、この付録の後半の「 [interval リテラル構文](../../../odbc/reference/appendixes/interval-literal-syntax.md)」を参照してください。  
  
 Interval リテラルエスケープシーケンスは、データソースで interval データ型がサポートされている場合にサポートされます。 アプリケーションは、これらのデータ型がサポートされているかどうかを判断するために**SQLGetTypeInfo**を呼び出す必要があります。
