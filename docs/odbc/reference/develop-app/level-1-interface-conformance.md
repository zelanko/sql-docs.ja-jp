---
title: レベル1のインターフェイスの準拠 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05cf381ccbb8c0747db88259acfb4ba218d3e0ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135011"
---
# <a name="level-1-interface-conformance"></a>レベル 1 インターフェイスの適合性
レベル1のインターフェイスの準拠レベルには、コアインターフェイスの準拠レベルの機能に加え、OLTP リレーショナル DBMS で通常使用できるトランザクションなどの追加機能が含まれています。 レベル1のインターフェイスに準拠したドライバーを使用すると、アプリケーションは、コアインターフェイスの準拠レベルの機能に加えて、次の操作を実行できます。  
  
|||  
|-|-|  
|101|データベースのテーブルとビューのスキーマを指定します (2 つの部分で構成される名前を使用)。 (詳細については、「[レベル2のインターフェイスの準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)」の3部構成の名前付け機能201を参照してください)。|  
|102|ODBC 関数の非同期実行を呼び出します (該当する ODBC 関数がすべて同期されている場合、または特定の接続で非同期の場合)。|  
|103|スクロール可能なカーソルを使用して、前方参照専用以外のメソッドで結果セットにアクセスできるようにするには、SQL_FETCH_NEXT 以外の*Fetchorientation*引数を指定して**sqlfetchscroll**を呼び出します。 (SQL_FETCH_BOOKMARK *Fetchorientation*は、[レベル2のインターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)の機能204にあります)。|  
|104|**Sqlprimarykeys**を呼び出して、テーブルの主キーを取得します。|  
|105|ストアドプロシージャを ODBC エスケープシーケンスを通じてプロシージャ呼び出しに使用し、 **SQLProcedureColumns**および**sqlprocedures**を呼び出してストアドプロシージャに関するデータ辞書にクエリを実行します。 (データソースにプロシージャを作成して格納するプロセスは、このドキュメントの範囲外です)。|  
|106|**SQLBrowseConnect**を呼び出して、使用可能なサーバーを対話形式で参照して、データソースに接続します。|  
|107|SQL ステートメントの代わりに ODBC 関数を使用して、特定のデータベース操作を実行します。 **SQLSetPos**では SQL_POSITION と SQL_REFRESH です。|  
|108|**Sqlmoreresults**を呼び出して、バッチおよびストアドプロシージャによって生成された複数の結果セットの内容にアクセスできるようにします。|  
|109|**SQLEndTran**で、真の原子性と SQL_ROLLBACK を指定する機能を使用して、複数の ODBC 関数にまたがるトランザクションを区切ります。|
