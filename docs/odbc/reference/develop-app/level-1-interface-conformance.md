---
title: インターフェイスへの準拠レベル 1 |Microsoft ドキュメント
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: faae1bf56dd28f83fa3fec5c340bcf67c302def3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="level-1-interface-conformance"></a>レベル 1 インターフェイスへの準拠
レベル 1 のインターフェイスへの準拠レベルには、コア インターフェイスへの準拠の機能レベルと、OLTP リレーショナル DBMS で通常利用できるトランザクションなどの追加機能が含まれています。 レベル 1 – インターフェイスに準拠するドライバーは、コア インターフェイスへの準拠レベルの機能に加えて、次の操作をアプリケーションを使用できます。  
  
|||  
|-|-|  
|101|データベースのスキーマのテーブルおよびビュー (2 部構成の名前付けを使用) を指定します。 (詳細については、機能の 201 3 部構成の名前付けを参照してください[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md))。|  
|102|該当する ODBC 関数が、すべての同期または非同期すべて 1 つの接続を ODBC 関数の場合は true。 非同期実行を呼び出します。|  
|103|スクロール可能なカーソルを使用して、それによってによって結果セットのメソッドで順方向専用、以外の呼び出しへのアクセスを実現**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_NEXT 以外の引数。 (、SQL_FETCH_BOOKMARK *FetchOrientation*機能 204 が[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md))。|  
|104|呼び出して、テーブルの主キーを入手**SQLPrimaryKeys**です。|  
|105|プロシージャ呼び出しについて、ODBC エスケープ シーケンスの実行中のストアド プロシージャを使用して呼び出すことによって、ストアド プロシージャに関するデータ ディクショナリをクエリ**SQLProcedureColumns**と**SQLProcedures**です。 (プロシージャの作成し、データ ソースに格納されているプロセスは、このドキュメントの範囲外です)|  
|106|対話形式で呼び出すことによって、使用可能なサーバーを参照することにより、データ ソースに接続**SQLBrowseConnect**です。|  
|107|データベースの特定の操作を実行する SQL ステートメントではなく ODBC 関数を使用: **SQLSetPos** SQL_POSITION と SQL_REFRESH を使用します。|  
|108|呼び出して、バッチおよびストアド プロシージャは、によって生成された複数の結果セットの内容にアクセスできるように**SQLMoreResults**です。|  
|109|True 原子性と SQL_ROLLBACK を指定することで複数の ODBC 関数にまたがるトランザクションを区切るため**SQLEndTran**です。|
