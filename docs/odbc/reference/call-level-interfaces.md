---
title: "呼び出しレベル インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e22537b5ce7b2b1ecfdf579e78859812895671c2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="call-level-interfaces"></a>呼び出しレベルのインターフェイス
最終的な手法、DBMS に SQL ステートメントを送信するは、呼び出しレベル インターフェイス (CLI) を使用します。 呼び出しレベルのインターフェイスは、アプリケーション プログラムによって呼び出すことができる DBMS 関数のライブラリを提供します。 したがって、他のプログラミング言語で SQL を合成するのではなく呼び出しレベルのインターフェイスがに似ていますが、日常的なライブラリのほとんどのプログラマは、文字列、I/O、または C. 注 embedded SQL をサポートするその Dbms での数値演算ライブラリなど、使用することに慣れて呼び出しレベルのインターフェイスを呼び出し先がプリによって生成されたが既にあります。 ただし、これらの呼び出しには、記載されていないと予告なく変更へのサブジェクトがします。  
  
 呼び出しレベルのインターフェイスは、クライアント/サーバー アーキテクチャのアプリケーション (クライアント) が 1 台のコンピューター上に存在し、別のコンピューター上の DBMS (サーバー) のよく使用されます。 アプリケーションが、ローカル システムで CLI 関数を呼び出すし、処理のため、DBMS にそれらの呼び出しをネットワーク経由で送信されます。  
  
 呼び出しレベルのインターフェイス似ていますが動的 SQL への SQL ステートメントは、実行時に処理するため、DBMS に渡されるとは異なり、埋め込まれた SQL 全体として埋め込まれた SQL ステートメントがないおよびプリは必要ありません。  
  
 通常、呼び出しレベルのインターフェイスを使用するには、次の手順が含まれます。  
  
1.  アプリケーションでは、DBMS に接続する CLI 関数を呼び出します。  
  
2.  アプリケーションが SQL ステートメントがビルドされ、バッファーに格納します。 準備と実行の DBMS にステートメントを送信する 1 つ以上の CLI 関数を呼び出します。  
  
3.  ステートメントが SELECT ステートメントの場合は、アプリケーションは、結果を返すため、アプリケーションのバッファーで CLI 関数を呼び出します。 通常、この関数を返します 1 行または 1 つの列のデータ、時にします。  
  
4.  アプリケーションでは、DBMS から切断する CLI 関数を呼び出します。

