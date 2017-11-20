---
title: "SQL モジュール |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f37ab932ef230d29a5db23aec920230de0443e37
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-modules"></a>SQL モジュール
DBMS に SQL ステートメントを送信するための 2 番目の手法では、モジュールを使用します。 簡単に、モジュールは、ホストのプログラミング言語から呼び出されるプロシージャのグループで構成されます。 各プロシージャには、1 つの SQL ステートメントが含まれています。 し、データとが渡されるプロシージャからパラメーターを使用します。  
  
 モジュールは、アプリケーション コードにリンクされているオブジェクト ライブラリと考えることができます。 ただし、正確に手順と、アプリケーションの残りの部分はリンク方法は、実装によって異なります。 など、プロシージャをオブジェクト コードにコンパイルされ、アプリケーション コードに直接リンクされている可能性があります、コンパイルされ、DBMS と、アプリケーション コード内にプランの識別子にアクセスする呼び出しに格納されている可能性があります。 または実行時に、解釈される可能性があります。  
  
 モジュールの主な利点は、プログラミング言語からの SQL ステートメントを明確に分離することです。 理論上は、もう一方を変更することがなく 1 つを変更し、単に再リンクして可能な場合があります。

