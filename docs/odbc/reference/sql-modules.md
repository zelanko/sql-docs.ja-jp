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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 351d1c6a34413b385bd76dfebb009b34c4c0f150
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280428"
---
# <a name="sql-modules"></a>SQL モジュール
SQL ステートメントを DBMS に送信するための2つ目の方法は、モジュールを使用することです。 簡単に言うと、モジュールは、ホストプログラミング言語から呼び出されるプロシージャのグループで構成されます。 各プロシージャには1つの SQL ステートメントが含まれており、パラメーターを使用してプロシージャとの間でデータが渡されます。  
  
 モジュールは、アプリケーションコードにリンクされているオブジェクトライブラリと考えることができます。 ただし、プロシージャとアプリケーションの他の部分がどのようにリンクされているかは、実装に依存します。 たとえば、プロシージャをオブジェクトコードにコンパイルし、アプリケーションコードに直接リンクすることができます。このプロシージャをコンパイルして DBMS に格納し、アプリケーションコードに配置されたアクセスプラン識別子を呼び出すか、実行時に解釈することができます。  
  
 モジュールの主な利点は、プログラミング言語から SQL ステートメントを明確に分離することです。 理論的には、もう一方を変更せずに変更し、単に再リンクすることができます。
