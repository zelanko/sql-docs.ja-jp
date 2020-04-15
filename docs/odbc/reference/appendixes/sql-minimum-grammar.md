---
title: SQL 最小文法 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20eee34feadb8e3140f25019ec6b0d036ff02e14
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304993"
---
# <a name="sql-minimum-grammar"></a>SQL の最小限の文法
このセクションでは、ODBC ドライバーがサポートする必要がある最小の SQL 構文について説明します。 このセクションで説明する構文は、SQL-92 のエントリ レベル構文のサブセットです。  
  
 アプリケーションは、このセクションの任意の構文を使用でき、ODBC 準拠のドライバーがその構文をサポートすることを保証します。 このセクションに含まれていない SQL-92 の追加機能がサポートされているかどうかを確認するには、アプリケーションはSQL_SQL_CONFORMANCE情報の種類を指定して**SQLGetInfo**を呼び出す必要があります。 ドライバーが SQL-92 準拠レベルに準拠していない場合でも、アプリケーションは、このセクションで説明されている構文を使用できます。 一方、ドライバーは、SQL-92 レベルに準拠している場合、そのレベルに含まれるすべての構文をサポートします。 ここで説明する最小文法は、最小 SQL-92 準拠レベルの純粋なサブセットであるため、このセクションの構文が含まれます。 アプリケーションは、サポートされている SQL-92 レベルを認識したら、その機能に対応する個別の情報の種類を使用して**SQLGetInfo**を呼び出すことによって、上位レベルの機能がサポートされているかどうかを判断できます ( 存在する場合) 。  
  
 読み取り専用のデータ ソースでのみ動作するドライバーは、データの変更に関するこのセクションに含まれる文法のこれらの部分をサポートしていない可能性があります。 アプリケーションは、SQL_DATA_SOURCE_READ_ONLY情報型を指定して**SQLGetInfo**を呼び出すことによって、データ ソースが読み取り専用かどうかを判断できます。  
  
## <a name="statement"></a>ステートメント  
 *テーブルステートメントを作成*します: :=  
  
 テーブル*の作成 ベース テーブル名*  
  
 (*列識別子データ型*[*,列識別子データ型*].)  
  
> [!IMPORTANT]  
>  *作成テーブル ステートメント*の*データ型*として、アプリケーションは**SQLGetTypeInfo**によって返される結果セットのTYPE_NAME列のデータ型を使用する必要があります。  
  
 *削除ステートメント検索*::=  
  
 *テーブル名*から削除 [WHERE*検索条件*]  
  
 *ドロップテーブルステートメント*::=  
  
 ドロップ テーブル*ベース テーブル名*  
  
 *挿入ステートメント*::=  
  
 *テーブル名*に挿入 [(*列識別子*[列*識別子]、列識別子*[.])]     VALUES (*挿入値*[,*挿入値*].)  
  
 *select-statement* ::=  
  
 [すべて&#124;異なる]*選択リストを選択します。*  
  
 FROM*テーブル参照リスト*  
  
 [WHERE*検索条件*]  
  
 [*句順 ]*  
  
 *ステートメント*::=*テーブル作成ステートメント*  
  
 &#124;*削除ステートメント検索*  
  
 *&#124;テーブルステートメント*  
  
 *挿入ステートメント&#124;*  
  
 *&#124;選択ステートメント*  
  
 *&#124;更新ステートメント検索*  
  
 *ステートメントの更新 - 検索*  
  
 *テーブル名を*更新  
  
 SET*列識別子*= {*式*&#124; NULL }  
  
 [,*列識別子*= {*式*&#124; NULL}  
  
 [WHERE*検索条件*]  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL ステートメントで使用される要素](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [データ型のサポート](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [パラメーターのデータ型](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [パラメーター マーカー](../../../odbc/reference/appendixes/parameter-markers.md)
