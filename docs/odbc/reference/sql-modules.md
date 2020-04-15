---
title: SQL モジュール |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280428"
---
# <a name="sql-modules"></a>SQL モジュール
SQL ステートメントを DBMS に送信する 2 番目の方法は、モジュールを使用することです。 簡単に言うと、モジュールはホスト プログラミング言語から呼び出されるプロシージャのグループで構成されます。 各プロシージャーには単一の SQL ステートメントが含まれ、プロシージャーとの間でパラメーターを介してデータが渡されます。  
  
 モジュールは、アプリケーション コードにリンクされたオブジェクト ライブラリと考えることができます。 ただし、プロシージャとアプリケーションの残りの部分がどのようにリンクされているかは、実装に依存します。 たとえば、プロシージャをオブジェクト コードにコンパイルしてアプリケーション コードに直接リンクしたり、DBMS にコンパイルして格納したり、アプリケーション コードに配置されたアクセス プラン識別子を呼び出したり、実行時に解釈したりできます。  
  
 モジュールの主な利点は、SQL ステートメントとプログラミング言語を明確に分離することです。 理論的には、他方を変更せずに1つを変更し、単にそれらを再リンクすることが可能であるべきです。
