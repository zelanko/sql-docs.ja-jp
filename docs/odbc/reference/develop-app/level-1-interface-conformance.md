---
title: レベル 1 インターフェイス準拠 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d31d5fe8aea1df4e7937104580efb820ba6f031
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306183"
---
# <a name="level-1-interface-conformance"></a>レベル 1 インターフェイスの適合性
レベル 1 のインターフェイス準拠レベルには、コア インターフェイス準拠レベル機能と、通常 OLTP リレーショナル DBMS で使用できるトランザクションなどの追加機能が含まれます。 レベル 1 のインターフェイスに準拠するドライバーは、コア インターフェイス準拠レベルの機能に加えて、アプリケーションは、次の操作を実行できます。  
  
|||  
|-|-|  
|101|データベーステーブルとビューのスキーマを指定します(2 つの部分から構成される名前付けを使用)。 (詳細については、「レベル 2[インターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)」の 3 部構成の名前付け機能 201 を参照してください)。|  
|102|ODBC 関数の真の非同期実行を呼び出します (該当する ODBC 関数がすべて同期または非同期の場合)。|  
|103|スクロール可能なカーソルを使用すると、SQL_FETCH_NEXT以外の*FetchOrientation*引数を指定して**SQLFetchScroll**を呼び出すことによって、前方専用以外のメソッドの結果セットにアクセスできます。 (SQL_FETCH_BOOKMARK *FetchOrientation*は、レベル 2[のインターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)の機能 204 にあります。|  
|104|SQLPrimaryKeys を呼び出してテーブルの**主キーを**取得します。|  
|105|ストアド プロシージャを使用して、プロシージャ呼び出しに対して ODBC エスケープ シーケンスを使用し、**ストアド プロシージャ**に関するデータ ディクショナリをクエリ**します**。 (データ ソース上でプロシージャを作成して格納するプロセスは、このドキュメントの範囲外です)。|  
|106|**SQLBrowseConnect**を呼び出して、使用可能なサーバーを対話的に参照してデータ ソースに接続します。|  
|107|SQL ステートメントの代わりに ODBC 関数を使用して、SQL_REFRESH SQL_POSITION 特定のデータベース**操作を実行**します。|  
|108|バッチおよびストアド プロシージャによって生成された複数の結果セットの内容にアクセスするには、 **SQLMoreResults**を呼び出します。|  
|109|複数の ODBC 関数にまたがるトランザクションを、真の原子性と**SQLEndTran**でSQL_ROLLBACK指定する機能を使用して区切ります。|
