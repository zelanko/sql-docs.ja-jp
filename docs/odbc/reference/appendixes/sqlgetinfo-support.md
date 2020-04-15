---
title: サポート |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a21c035a14814f51d4344894ef253b2cc844f4c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307803"
---
# <a name="sqlgetinfo-support"></a>SQLGetInfo のサポート
ODBC 2 の場合。*x*アプリケーションは、ODBC 3 *.x*ドライバーに*InfoType***SQLGetInfo**を呼び出します。  
  
|*Infotype*|戻り値|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0)**注:** この情報型は非推奨ではありません。右側の列のビットマスクは非推奨です。|データ ソースでサポートされている**ALTER TABLE**ステートメント内の句を列挙する SQLINTEGER ビットマスク。<br /><br /> サポートされる句を決定するには、次のビットマスクを使用します。<br /><br /> SQL_AT_DROP_COLUMN = 列を削除する機能がサポートされています。 これがカスケードまたは制限動作を生じるかどうかは、ドライバー定義です。 (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN = 1 つの ALTER TABLE ステートメントに複数の列を追加する機能がサポートされています。 このビットは、他のSQL_AT_ADD_COLUMN_XXXビットまたはSQL_AT_CONSTRAINT_XXXビットとは結合されません。 (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> 情報の種類は ODBC 1.0 で導入されました。各ビットマスクには、導入されたバージョンがラベル付けされています。|サポートされているフェッチ方向オプションを列挙する SQLINTEGER ビットマスク。<br /><br /> 次のビットマスクは、どのオプションがサポートされているかを決定するためにフラグと組み合わせて使用されます。<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|サポートされているロックの種類を列挙する SQLINTEGER ビットマスクで **、sqlSetPos**の*fLock*引数に対して使用できます。<br /><br /> 次のビットマスクは、どのロック・タイプがサポートされているかを判別するために、フラグと組み合わせて使用されます。<br /><br /> SQL_LCK_NO_CHANGESQL_LCK_EXCLUSIVESQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|ODBC 準拠のレベルを示す SQLSMALLINT 値。<br /><br /> SQL_OAC_NONE = なし<br /><br /> SQL_OAC_LEVEL1 = サポートされるレベル 1<br /><br /> SQL_OAC_LEVEL2 = サポートされるレベル 2|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|ドライバーによってサポートされている SQL 文法を示す SQLSMALLINT 値。 SQL 準拠レベルの定義については、「[付録 C: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」を参照してください。<br /><br /> SQL_OSC_MINIMUM = サポートされる最小文法<br /><br /> SQL_OSC_CORE = サポートされるコア文法<br /><br /> SQL_OSC_EXTENDED = 拡張文法がサポートされています|  
|SQL_POS_OPERATIONS (ODBC 2.0)|SQLINTEGER ビットマスクで **、SQLSetPos**でサポートされている操作を列挙します。<br /><br /> 次のビットマスクは、どのオプションがサポートされているかを決定するためにフラグと組み合わせて使用されます。<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|サポートされている位置指定 SQL ステートメントを列挙する SQLINTEGER ビットマスク。<br /><br /> サポートされるステートメントを判別するには、次のビットマスクを使用します。<br /><br /> SQL_PS_POSITIONED_DELETE、SQL_PS_POSITIONED_UPDATE、SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|カーソルでサポートされている同時実行制御オプションを列挙する SQLINTEGER ビットマスク。<br /><br /> サポートされるオプションを決定するには、次のビットマスクを使用します。<br /><br /> SQL_SCCO_READ_ONLY = カーソルは読み取り専用です。 更新は許可されません。<br /><br /> SQL_SCCO_LOCK = カーソルは、行を確実に更新するために十分な最低レベルのロックを使用します。<br /><br /> SQL_SCCO_OPT_ROWVER = カーソルはオプティミスティック同時実行制御を使用し、SQLBase ROWID や Sybase TIMESTAMP などの行バージョンを比較します。<br /><br /> SQL_SCCO_OPT_VALUES = カーソルはオプティミスティック同時実行制御を使用して値を比較します。|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|アプリケーションが **、SQLSetPos**または位置指定更新ステートメントまたは削除ステートメントを使用して静的カーソルまたはキーセット ドリブン カーソルに加えた変更を、そのアプリケーションによって検出できるかどうかを列挙する SQLINTEGER ビットマスク。<br /><br /> SQL_SS_ADDITIONS = 追加された行はカーソルに対して可視になります。カーソルはこれらの行までスクロールできます。 これらの行がカーソルに追加される場所は、ドライバーに依存します。<br /><br /> SQL_SS_DELETIONS = 削除された行はカーソルから使用できなくなり、結果セットに 「穴」を残しません。削除された行からカーソルをスクロールした後は、その行に戻ることはできません。<br /><br /> SQL_SS_UPDATES = 行の更新はカーソルから見えます。カーソルがスクロールして更新された行に戻った場合、カーソルによって返されるデータは更新されたデータであり、元のデータではありません。 このオプションは、キーを更新しないキーセット ドリブン カーソルの静的カーソルまたは更新にのみ適用されます。 このオプションは、動的カーソルに適用されないか、または混合カーソルでキーが変更される場合には適用されません。<br /><br /> アプリケーションが、同じアプリケーション内の他のカーソルを含む他のユーザーによって結果セットに加えられた変更を検出できるかどうかは、カーソルの種類によって異なります。|  
  
 ODBC 3 *.x*ドライバーを使用する ODBC 3 *.x*アプリケーションでは、前の表で説明した*InfoType*引数を使用して**SQLGetInfo**を呼び出す必要はありませんが、次の段落に記載されている ODBC 3 *.x* *InfoType*引数を使用する必要があります。 ODBC 2 で使用される*インフォタイプ*引数の間には、1 対 1 の対応はありません。*x*と ODBC 3 *.x*で使用されるもの。 ODBC 2 で動作する ODBC 3 *.x*アプリケーション。*x*ドライバは、前に説明した*インフォタイプ*引数を使用する必要があります。  
  
 前の表の情報タイプの一部は、カーソル属性情報タイプを優先して非推奨です。 これらの非推奨の情報タイプは、SQL_FETCH_DIRECTION、SQL_LOCK_TYPES、SQL_POS_OPERATIONS、SQL_POSITIONED_STATEMENTS、SQL_SCROLL_CONCURRENCY、およびSQL_STATIC_SENSITIVITYです。 新しいカーソル属性タイプはSQL_XXX_CURSOR_ATTRIBUTES2SQL_XXX_CURSOR_ATTRIBUTES1andされ、XXX は DYNAMIC、FORWARD_ONLY、KEYSET_DRIVEN、または STATIC に等しくなります。 新しい型のそれぞれは、1 つのカーソルの種類のドライバーの機能を示します。 これらのオプションの詳細については[、SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明を参照してください。
