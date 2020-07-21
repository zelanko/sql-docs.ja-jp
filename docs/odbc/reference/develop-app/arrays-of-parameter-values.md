---
title: パラメーター値の配列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb9389c769e3a7bb0c39959a559531e8051a7bec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298802"
---
# <a name="arrays-of-parameter-values"></a>パラメーター値の配列
多くの場合、アプリケーションでパラメーターの配列を渡すと便利です。 たとえば、パラメーターの配列とパラメーター化された**INSERT**ステートメントを使用すると、アプリケーションは一度に複数の行を挿入できます。 配列の使用にはいくつかの利点があります。 まず、多数のステートメントのデータが1つのパケットで送信されるため、ネットワークトラフィックが削減されます (データソースでパラメーター配列がネイティブにサポートされている場合)。 2つ目のデータソースの中には、同じ数の独立した SQL ステートメントを実行するよりも、配列を使用して SQL ステートメントを実行できることがあります。 最後に、データが配列に格納されている場合、画面データの場合と同様に、アプリケーションでは、特定の列のすべての行をバインドして、1つのステートメントを実行することで、 **SQLBindParameter**を1回だけ呼び出すことができます。  
  
 残念ながら、多くのデータソースでパラメーター配列がサポートされていません。 ただし、ドライバーは、パラメーター値の各セットに対して SQL ステートメントを1回実行することによって、パラメーター配列をエミュレートできます。 これにより、ドライバーは、パラメーターセットごとに1回実行するように計画するステートメントを準備できるため、処理速度が向上する可能性があります。 また、アプリケーションコードが簡素化される可能性もあります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [パラメーターのバインディング配列](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [パラメーターの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
