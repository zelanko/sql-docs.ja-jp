---
title: 呼び出しレベルのインターフェイス |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6c37084ad91a931c4479ecf826c5cb554765412
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135673"
---
# <a name="call-level-interfaces"></a>コールレベル インターフェイス
SQL ステートメントを DBMS に送信するための最後の手法は、呼び出しレベルのインターフェイス (CLI) を使用することです。 呼び出しレベルのインターフェイスには、アプリケーションプログラムから呼び出すことができる DBMS 関数のライブラリが用意されています。 そのため、SQL を別のプログラミング言語と blend するのではなく、呼び出しレベルのインターフェイスは、C の文字列、i/o、または数値演算ライブラリなど、ほとんどのプログラマが使用することに慣れているルーチンライブラリに似ています。埋め込み SQL をサポートする Dbms には、呼び出しレベルのインターフェイスが既にあります。 ただし、これらの呼び出しは非公開であり、予告なしに変更される可能性があります。  
  
 呼び出しレベルのインターフェイスは、クライアント/サーバーアーキテクチャでよく使用されます。このアーキテクチャでは、アプリケーションプログラム (クライアント) が1台のコンピューター上に存在し、DBMS (サーバー) が別のコンピューター上に存在します。 アプリケーションはローカルシステムで CLI 関数を呼び出し、これらの呼び出しはネットワーク経由で DBMS に送信され、処理されます。  
  
 呼び出しレベルのインターフェイスは動的 SQL に似ていますが、SQL ステートメントは実行時に処理のために DBMS に渡されますが、埋め込み sql ステートメントが存在せず、プリコンパイラは不要であるという点で、埋め込み SQL とは異なります。  
  
 通常、呼び出しレベルのインターフェイスを使用するには、次の手順を実行します。  
  
1.  アプリケーションは、CLI 関数を呼び出して DBMS に接続します。  
  
2.  アプリケーションは、SQL ステートメントを作成し、バッファーに格納します。 次に、1つまたは複数の CLI 関数を呼び出して、準備と実行のためにステートメントを DBMS に送信します。  
  
3.  ステートメントが SELECT ステートメントである場合、アプリケーションは CLI 関数を呼び出して、結果をアプリケーションバッファーに返します。 通常、この関数は、一度に1行または1列のデータを返します。  
  
4.  アプリケーションは、CLI 関数を呼び出して、DBMS から切断します。
