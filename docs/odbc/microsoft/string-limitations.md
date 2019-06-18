---
title: 文字列の制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 003cd318d6db54c7547375219805c63cfc4ce249
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63269855"
---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメントの文字列の最大長は、65,000 文字です。  
  
 Microsoft Access ドライバーを使用すると、(単一引用符、いない二重引用符) で sql-92 の文字列定数のみがサポートされます。  
  
 パイプ文字 (&#124;) かどうか文字がバック引用符で囲まれているかどうか、文字列では使用できません。  
  
 相互運用性を最大に、アプリケーションが、パラメーターの文字列を渡す必要がありますのではなく渡す文字列を引用符で囲まれました。
