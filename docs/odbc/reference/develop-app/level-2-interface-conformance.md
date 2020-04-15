---
title: レベル 2 インターフェイス準拠 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ee57d716cbb93f855e1fd78d41bff62a681eb6c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306164"
---
# <a name="level-2-interface-conformance"></a>レベル 2 インターフェイスの適合性
レベル 2 のインターフェイス準拠レベルには、レベル 1 のインターフェイス準拠レベル機能と、次の機能が含まれます。  
  
|||  
|-|-|  
|201|データベーステーブルとビューの 3 つの部分から構成される名前を使用します。 (詳細については、「レベル 1 インターフェイス準拠」の 2 部構成の名前付けサポート機能[101](../../../odbc/reference/develop-app/level-1-interface-conformance.md)を参照してください)。|  
|202|動的パラメーターを記述する場合は **、SQLDescribeParam**を呼び出します。|  
|203|入力パラメータだけでなく、出力パラメータや入出力パラメータ、ストアドプロシージャの結果値も使用します。|  
|204|ブックマークの取得を含むブックマークを使用するには、列番号 0 で**SQLDescribeCol**と**SQLColAttribute**を呼び出します。SQL_FETCH_BOOKMARKに設定された*FetchOrientation*引数を使用して**SQLFetchScroll**を呼び出すことによって、ブックマークに基づいてフェッチします。また **、sqlBulkOperations**を呼び出して、ブックマーク操作によって更新、削除、およびフェッチを行い *、"操作"* 引数を SQL_UPDATE_BY_BOOKMARK、SQL_DELETE_BY_BOOKMARK、またはSQL_FETCH_BY_BOOKMARKに設定します。|  
|205|**SQLColumnPrivileges** **、SQLForeignKeys、** および**SQLTablePrivileges**を呼び出すことによって、データ ディクショナリに関する詳細情報を取得します。|  
|206|SQL ステートメントの代わりに ODBC 関数を使用して **、SQLBulkOperations**をSQL_ADDで呼び出したり **、sqlSetPos**をSQL_DELETEまたはSQL_UPDATEで呼び出して、追加のデータベース操作を実行します。 *(LockType*引数をSQL_LOCK_EXCLUSIVE またはSQL_LOCK_UNLOCK に設定した**SQLSetPos**への呼び出しのサポートは、準拠レベルの一部ではありませんが、オプションの機能です。|  
|207|指定された個々のステートメントに対して ODBC 関数の非同期実行を有効にします。|  
|208|**SQLSpecialColumns**を呼び出して、テーブルの行を識別する列SQL_ROWVERを取得します。 (詳細については、[コア インターフェイス準拠](../../../odbc/reference/develop-app/core-interface-conformance.md)の機能 20 としてSQL_BEST_ROWIDに設定された*識別子の型*引数を持つ**SQLSpecialColumns**のサポートを参照してください。|  
|209|SQL_ATTR_CONCURRENCYステートメント属性を、SQL_CONCUR_READ_ONLY以外の値を少なくとも 1 つ設定します。|  
|210|ログイン要求と SQL クエリ (SQL_ATTR_LOGIN_TIMEOUT とSQL_ATTR_QUERY_TIMEOUT) をタイムアウトする機能。|  
|211|既定の分離レベルを変更する機能。"シリアル化可能" レベルの分離でトランザクションを実行する機能。|
