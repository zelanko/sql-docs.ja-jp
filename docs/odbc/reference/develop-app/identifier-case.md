---
title: 識別子のケース |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66218fb955a4133a5c689f72ab8f4b96504c9bd2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908853"
---
# <a name="identifier-case"></a>識別子のケース
SQL ステートメントおよびカタログ関数の引数は、識別子と引用符で囲まれた識別子を指定できますいずれかの大文字小文字を区別や、アプリケーションを呼び出すことによって判別される、 **SQLGetInfo** SQL_IDENTIFIER_CASE SQL_QUOTED_ とIDENTIFIER_CASE オプションです。  
  
 これらのオプションは次の 4 つの可能な戻り値: 1 つあることを示す識別子または引用符で囲まれた識別子の大文字と小文字が区別し、次の 3 つを示すは区別されません。 さらに、大文字小文字が区別されない 3 つの値には、識別子がシステム カタログに格納されているケースがについて説明します。 アプリケーションが、カタログ関数の結果を表示するときなど、表示目的のみに関連がシステム カタログの識別子を格納する方法識別子の大文字小文字の区別は変更されません。
