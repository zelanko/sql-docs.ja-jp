---
title: "識別子のケース |Microsoft ドキュメント"
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
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17c1d7658b313860fdc3abfe0c756a38046dbfc4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="identifier-case"></a>識別子のケース
SQL ステートメントおよびカタログ関数の引数は、識別子と引用符で囲まれた識別子を指定できますいずれかの大文字小文字を区別や、アプリケーションを呼び出すことによって判別される、 **SQLGetInfo** SQL_IDENTIFIER_CASE SQL_QUOTED_ とIDENTIFIER_CASE オプションです。  
  
 これらのオプションは次の 4 つの可能な戻り値: 1 つあることを示す識別子または引用符で囲まれた識別子の大文字と小文字が区別し、次の 3 つを示すは区別されません。 さらに、大文字小文字が区別されない 3 つの値には、識別子がシステム カタログに格納されているケースがについて説明します。 アプリケーションが、カタログ関数の結果を表示するときなど、表示目的のみに関連がシステム カタログの識別子を格納する方法識別子の大文字小文字の区別は変更されません。
