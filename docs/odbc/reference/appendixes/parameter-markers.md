---
title: "パラメーター マーカー |Microsoft ドキュメント"
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58bde9217e293f1f3fb0a68a7cbf2c4aef6aac1e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="parameter-markers"></a>パラメーター マーカー
SQL 92 仕様に従って、アプリケーションは、次の場所にパラメーター マーカーを配置できません。 包括的な一覧は、SQL 92 仕様を参照してください。  
  
-   **選択**一覧  
  
-   両方と*式*で、*比較述語*  
  
-   バイナリ演算子のオペランドは両方として  
  
-   最初と 2 番目のオペランドとして、 **BETWEEN**操作  
  
-   最初と 3 番目の両方のオペランドとして、 **BETWEEN**操作  
  
-   式との最初の値の両方として、 **IN**操作  
  
-   単項演算子のオペランドとして + または – 操作  
  
-   引数として、*セット関数リファレンス*  
  
 パラメーター マーカーの詳細については、SQL 92 仕様を参照してください。 パラメーターの詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。
