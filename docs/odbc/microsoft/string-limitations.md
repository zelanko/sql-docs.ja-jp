---
title: "文字列の制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 260a530210b2e336067f2036f632cf347c1654f9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメントの文字列の最大長は、65,000 文字です。  
  
 Microsoft Access ドライバーを使用する場合 (単一引用符でない二重引用符) で sql-92 の文字列定数のみがサポートされています。  
  
 パイプ文字 (&#124;) バック引用符で囲まれた文字が囲まれているかどうかどうか、文字列では使用できません。  
  
 相互運用性を最大にするため、アプリケーションが、パラメーターの文字列を渡す必要がありますではなく渡すには、文字列が引用符で囲まれました。
