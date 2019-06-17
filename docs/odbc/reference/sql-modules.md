---
title: SQL モジュール |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30c116878049c4f6a8f36e988731ab641e03c6d7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63232776"
---
# <a name="sql-modules"></a>SQL モジュール
DBMS に SQL ステートメントを送信するための 2 番目の手法では、モジュールを使用します。 簡単に、モジュールは、ホストのプログラミング言語から呼び出されるプロシージャのグループで構成されます。 各プロシージャには、1 つの SQL ステートメントが含まれています。 され、データがパラメーターを使用して、プロシージャからを渡されます。  
  
 モジュールは、アプリケーション コードにリンクされているオブジェクト ライブラリとして考えることができます。 ただし、正確に手順と、アプリケーションの残りの部分はリンク方法とは実装によって異なります。 たとえば、プロシージャのオブジェクトのコードにコンパイルし、アプリケーション コードに直接リンクされている可能性があります、コンパイルされ、アプリケーション コード内に配置プラン識別子へのアクセスを呼び出すと DBMS に格納されている可能性があります。 またはが実行時に解釈できます。  
  
 モジュールの主な利点は、プログラミング言語から SQL ステートメントを明確に分離することです。 理論上を単純に再リンクして、もう一方を変更することがなく 1 つを変更可能な場合があります。
