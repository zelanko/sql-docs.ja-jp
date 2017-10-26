---
title: "文字列の制限事項 |Microsoft ドキュメント"
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
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e6f9d8add08f80b59adaa42f02bc1da006356081
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメントの文字列の最大長は、65,000 文字です。  
  
 Microsoft Access ドライバーを使用する場合 (単一引用符でない二重引用符) で sql-92 の文字列定数のみがサポートされています。  
  
 パイプ文字 (&#124;) バック引用符で囲まれた文字が囲まれているかどうかどうか、文字列では使用できません。  
  
 相互運用性を最大にするため、アプリケーションが、パラメーターの文字列を渡す必要がありますではなく渡すには、文字列が引用符で囲まれました。

