---
title: "識別子の制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6bc9deecbd06b3bcb0aec9d3e0d3b8790c7af0b6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="identifiers-limitations"></a>識別子の制限事項
スペースまたは特殊記号が識別子が含まれる場合は、逆引用符で囲まれた識別子を囲む必要があります。 有効な名前は、うち最初の文字必要がありますスペースは使用できません、64 個の文字の文字列です。 有効な名前は、制御文字または次の特殊文字を含めることはできません。 ' &#124;です。# * ? [ ] . ! $ .  
  
 予約語に記載の付録 C での SQL 文法を使用しないでください、 *ODBC プログラマ リファレンス*(またはこれらの予約語の短い形式) として識別子 (つまり、テーブルまたは列名)、word の背面にで囲まれている場合を除き、引用符 (')。
