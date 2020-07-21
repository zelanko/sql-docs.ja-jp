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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fe7f6941e9ec9fba8b6698faaa18a678732dd6f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304957"
---
# <a name="interval-escape-sequences"></a>Interval のエスケープ シーケンス
ODBC では、間隔リテラルにエスケープシーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
 {*interval-リテラル*}  
  
 *Interval リテラル*の BNF 構文については、この付録の後半の「 [interval リテラル構文](../../../odbc/reference/appendixes/interval-literal-syntax.md)」を参照してください。  
  
 Interval リテラルエスケープシーケンスは、データソースで interval データ型がサポートされている場合にサポートされます。 アプリケーションは、これらのデータ型がサポートされているかどうかを判断するために**SQLGetTypeInfo**を呼び出す必要があります。
