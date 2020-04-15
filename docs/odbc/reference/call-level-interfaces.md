---
title: コールレベルインタフェース |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4288a278f745d533c92d3d45892753ef1a74c2b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306543"
---
# <a name="call-level-interfaces"></a>コールレベル インターフェイス
SQL ステートメントを DBMS に送信する最後の方法は、呼び出しレベルのインターフェイス (CLI) を使用します。 呼び出しレベルのインタフェースは、アプリケーション・プログラムから呼び出すことができる DBMS 関数のライブラリーを提供します。 したがって、呼び出しレベルのインターフェイスは、SQL を別のプログラミング言語とブレンドしようとするのではなく、C の文字列、I/O、または数学ライブラリなど、ほとんどのプログラマが使用するルーチン ライブラリに似ています。 ただし、これらの呼び出しは文書化されておらず、予告なしに変更される可能性があります。  
  
 呼び出しレベルのインターフェイスは、一般に、アプリケーション プログラム (クライアント) が 1 つのコンピュータに存在し、DBMS (サーバー) が別のコンピュータ上に存在するクライアント/サーバー アーキテクチャで使用されます。 アプリケーションはローカル・システム上の CLI 関数を呼び出し、それらの呼び出しは、処理のためにネットワークを介して DBMS に送信されます。  
  
 呼び出しレベルのインターフェースは動的 SQL と似ていますが、SQL ステートメントは実行時に処理のために DBMS に渡されますが、組み込み SQL ステートメントがなく、プリコンパイラーも必要ない点で、組み込み SQL 全体とは異なります。  
  
 呼び出しレベルのインターフェイスを使用するには、通常、次の手順を実行します。  
  
1.  アプリケーションは、DBMS に接続する CLI 関数を呼び出します。  
  
2.  アプリケーションは SQL ステートメントを作成し、バッファーに格納します。 その後、1 つ以上の CLI 関数を呼び出して、準備と実行のためにステートメントを DBMS に送信します。  
  
3.  ステートメントが SELECT ステートメントの場合、アプリケーションは CLI 関数を呼び出して、結果をアプリケーション・バッファーに戻します。 通常、この関数は、一度に 1 行または 1 列のデータを返します。  
  
4.  アプリケーションは、DBMS から切断する CLI 関数を呼び出します。
