---
title: SQL モジュール |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a345d64e7ed9353513ce67c71f5442d317df701f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sql-modules"></a>SQL モジュール
DBMS に SQL ステートメントを送信するための 2 番目の手法では、モジュールを使用します。 簡単に、モジュールは、ホストのプログラミング言語から呼び出されるプロシージャのグループで構成されます。 各プロシージャには、1 つの SQL ステートメントが含まれています。 し、データとが渡されるプロシージャからパラメーターを使用します。  
  
 モジュールは、アプリケーション コードにリンクされているオブジェクト ライブラリと考えることができます。 ただし、正確に手順と、アプリケーションの残りの部分はリンク方法は、実装によって異なります。 など、プロシージャをオブジェクト コードにコンパイルされ、アプリケーション コードに直接リンクされている可能性があります、コンパイルされ、DBMS と、アプリケーション コード内にプランの識別子にアクセスする呼び出しに格納されている可能性があります。 または実行時に、解釈される可能性があります。  
  
 モジュールの主な利点は、プログラミング言語からの SQL ステートメントを明確に分離することです。 理論上は、もう一方を変更することがなく 1 つを変更し、単に再リンクして可能な場合があります。
