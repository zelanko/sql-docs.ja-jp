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
ms.openlocfilehash: 1b5cef56cec30e5ad09500135e05884bf55d5dde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076226"
---
# <a name="sql-modules"></a>SQL モジュール
SQL ステートメントを DBMS に送信するための2つ目の方法は、モジュールを使用することです。 簡単に言うと、モジュールは、ホストプログラミング言語から呼び出されるプロシージャのグループで構成されます。 各プロシージャには1つの SQL ステートメントが含まれており、パラメーターを使用してプロシージャとの間でデータが渡されます。  
  
 モジュールは、アプリケーションコードにリンクされているオブジェクトライブラリと考えることができます。 ただし、プロシージャとアプリケーションの他の部分がどのようにリンクされているかは、実装に依存します。 たとえば、プロシージャをオブジェクトコードにコンパイルし、アプリケーションコードに直接リンクすることができます。このプロシージャをコンパイルして DBMS に格納し、アプリケーションコードに配置されたアクセスプラン識別子を呼び出すか、実行時に解釈することができます。  
  
 モジュールの主な利点は、プログラミング言語から SQL ステートメントを明確に分離することです。 理論的には、もう一方を変更せずに変更し、単に再リンクすることができます。
