---
title: 文字列の制限事項 |Microsoft ドキュメント
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
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 740a6688d80d104d483c67c6998d20ec204ab41f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメントの文字列の最大長は、65,000 文字です。  
  
 Microsoft Access ドライバーを使用する場合 (単一引用符でない二重引用符) で sql-92 の文字列定数のみがサポートされています。  
  
 パイプ文字 (&#124;) バック引用符で囲まれた文字が囲まれているかどうかどうか、文字列では使用できません。  
  
 相互運用性を最大にするため、アプリケーションが、パラメーターの文字列を渡す必要がありますではなく渡すには、文字列が引用符で囲まれました。
