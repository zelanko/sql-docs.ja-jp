---
title: "SQLGetInfo サポート |Microsoft ドキュメント"
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
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb9afa5b40ffa7628e04ee85e5ddc4f752e98935
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetinfo-support"></a>SQLGetInfo サポート
ODBC 2 時にします。*x*アプリケーション呼び出し**SQLGetInfo** ODBC 3*.x*ドライバー、*情報の種類*次の表に引数をサポートする必要があります。  
  
|*情報の種類*|返します。|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0)**注:**この情報の種類は推奨されていません。 右側にある列ビットマスクは推奨されなくなりました。|内の句を列挙する SQLINTEGER ビットマスク、 **ALTER TABLE**ステートメント、データ ソースによってサポートされています。<br /><br /> 以下のビットマスクを使用して、どの句がサポートされてを調べます。<br /><br /> SQL_AT_DROP_COLUMN = 列を削除する機能をサポートします。 この結果が cascade または動作を制限するかどうかは、ドライバーの定義です。 (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN、単一の ALTER TABLE ステートメントで複数の列のサポートを追加する機能を = です。 このビットは、他の SQL_AT_ADD_COLUMN_XXX bits または SQL_AT_CONSTRAINT_XXX bits と組み合わせないでください。 (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> 情報の種類が ODBC 1.0; で導入されました。各ビットマスクには、導入されたバージョンが付いています。|サポートされる fetch の方向オプションを列挙する SQLINTEGER ビットマスクです。<br /><br /> 以下のビットマスクを決定するオプションがサポートされているとフラグの組み合わせで使用されます。<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) (ODBC 1.0)、SQL_FD_FETCH_RELATIVE SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|サポートされているロックを列挙する SQLINTEGER ビットマスク型、 *fLock*引数**SQLSetPos**です。<br /><br /> 以下のビットマスクを決定するロックの種類がサポートされているとフラグの組み合わせで使用されます。<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|ODBC 準拠のレベルを示す SQLSMALLINT 値です。<br /><br /> SQL_OAC_NONE = なし<br /><br /> SQL_OAC_LEVEL1 レベル 1 のサポートを =<br /><br /> SQL_OAC_LEVEL2 レベル 2 のサポートを =|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|ドライバーでサポートされている SQL 文法を示す SQLSMALLINT 値です。 参照してください[付録 c: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)SQL への準拠レベルの定義についてはします。<br /><br /> 以上でなければなりませんサポートされている最低限の文法を =<br /><br /> SQL_OSC_CORE サポートされているコアの文法を =<br /><br /> SQL_OSC_EXTENDED サポート拡張の文法を =|  
|SQL_POS_OPERATIONS (ODBC 2.0)|サポートされている操作を列挙する SQLINTEGER ビットマスク**SQLSetPos**です。<br /><br /> 以下のビットマスクを決定するオプションがサポートされているフラグと組み合わせてでに使用されます。<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|サポートされている列挙 SQLINTEGER ビットマスクは、SQL ステートメントを配置します。<br /><br /> 以下のビットマスクを使用して、どのステートメントは、サポートを調べます。<br /><br /> SQL_PS_POSITIONED_DELETE、SQL_PS_POSITIONED_UPDATE、SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|カーソルのサポートされている同時実行制御オプションを列挙する SQLINTEGER ビットマスクです。<br /><br /> 以下のビットマスクを使用して、どのオプションがサポートされているを調べます。<br /><br /> SQL_SCCO_READ_ONLY = カーソルは読み取り専用です。 更新は許可されません。<br /><br /> SQL_SCCO_LOCK、行を更新することを確認するための十分なロックの最も低いレベルのカーソルの使用を = です。<br /><br /> SQL_SCCO_OPT_ROWVER SQLBase ROWID または Sybase タイムスタンプなどの行のバージョンを比較する、カーソルはオプティミスティック同時実行制御を = です。<br /><br /> SQL_SCCO_OPT_VALUES 値を比較する、カーソルはオプティミスティック同時実行制御を = です。|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|静的であるか、キーセット ドリブン カーソルのアプリケーションによって変更が行われたかどうか、SQLINTEGER ビットマスクを列挙する**SQLSetPos**または位置指定更新または削除ステートメントは、そのアプリケーションによって検出できます。<br /><br /> SQL_SS_ADDITIONS = 追加された行がカーソルに表示されます。これらの行にカーソルがスクロールできます。 ドライバーに依存するは、これらの行がカーソルに追加されます。<br /><br /> SQL_SS_DELETIONS = 削除された行がカーソルを使用できなくと、結果セット内の「穴」のままにしないでください削除された行からカーソルをスクロールする後は、その行に戻ることはできません。<br /><br /> SQL_SS_UPDATES = 行の更新が、カーソルに表示されます。カーソルからまでスクロールし、更新された行を返します、カーソルによって返されるデータが元のデータではなく、更新されたデータ。 このオプションは、キーを更新できませんキーセット ドリブン カーソルでのみに静的カーソルや更新プログラムを適用します。 このオプションは、動的カーソルやカーソルの混合をキーが変更された場合に適用されません。<br /><br /> アプリケーションが、同じアプリケーション内の他のカーソルを含む、他のユーザーごとに結果セットに加えられた変更を検出できるかどうかは、カーソルの種類によって異なります。|  
  
 ODBC 3*.x* ODBC 3 作業アプリケーション*.x*ドライバー呼び出す必要はありません**SQLGetInfo**で、*情報の種類*で引数の説明前述のテーブルが、ODBC 3 を使用する必要があります*.x* *情報の種類*引数は、次の段落に一覧表示します。 一対一の対応関係がない*情報の種類*ODBC 2 で使用される引数*。x* ODBC 3 で使用されるものと*.x*です。 ODBC 3*.x* ODBC 2 を使用するアプリケーション*。x*ドライバー、その一方で、使用する必要があります、*情報の種類*引数が以前に説明します。  
  
 カーソルの属性情報の種類を優先するため、前の表の情報の種類の一部は推奨されません。 これらには、種類は SQL_FETCH_DIRECTION、SQL_LOCK_TYPES、SQL_POS_OPERATIONS、SQL_POSITIONED_STATEMENTS、SQL_SCROLL_CONCURRENCY、および SQL_STATIC_SENSITIVITY 情報が使用されなくなりました。 新しい種類のカーソルの属性は、SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2、DYNAMIC、FORWARD_ONLY、KEYSET_DRIVEN、または静的 XXX と等しいです。 それぞれの新しい型には、ドライバーの機能は、1 つのカーソルの種類のことを示します。 これらのオプションの詳細については、次を参照してください。、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。

