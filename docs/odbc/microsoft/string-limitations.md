---
title: 文字列の制限 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306063"
---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメントの文字列の最大長は 65,000 文字です。  
  
 Access ドライバを使用する場合、SQL-92 文字列定数 (二重引用符ではなく単一引用符で囲む) のみがサポートされます。  
  
 パイプ文字 (&#124;) は、文字が引用符で囲まれているかどうかにかかわらず、文字列内で使用できません。  
  
 相互運用性を最大限に高めるには、アプリケーションは引用符で囲まれた文字列を渡すのではなく、パラメータで文字列を渡す必要があります。
