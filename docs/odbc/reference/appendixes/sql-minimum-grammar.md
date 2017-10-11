---
title: "SQL の文法 |Microsoft ドキュメント"
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c225ab76f4c67938590bd19f21bfafafa20742d8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-minimum-grammar"></a>SQL の文法
このセクションでは、ODBC ドライバーのサポートが必要な最低限の SQL 構文について説明します。 このセクションで説明する構文は、SQL 92 のエントリ レベルの構文のサブセットです。  
  
 アプリケーションでは、このセクションの内容の構文のいずれかを使用することができ、任意の ODBC 準拠のドライバーがその構文をサポートする確実に実行します。 このセクションではなく、sql-92 の追加の機能がサポートされているかどうかを決定するには、アプリケーションを呼び出す必要があります**SQLGetInfo** SQL_SQL_CONFORMANCE 情報の種類とします。 ドライバーは、任意の sql-92 準拠レベルを準拠していない、場合でも、アプリケーションはこのセクションで説明する構文を使用できます。 その一方で、ドライバーは、SQL 92 レベルに準拠している場合、そのレベルに含まれるすべての構文をサポートします。 ここで説明されている最低限の文法が最下位の sql-92 準拠レベルの純粋なサブセットであるためここに、構文を含めます。 アプリケーションは、サポートされている SQL 92 レベルを知っていれば後、かどうかより高いレベルの機能はサポートされて (存在する場合) を呼び出してを決定できる**SQLGetInfo**とその機能に対応する個々 の情報の種類。  
  
 読み取り専用のデータ ソースでのみ動作するドライバーがデータの変更を処理するこのセクションの内容の文法の一部をサポートしていません。 アプリケーションでは、呼び出すことによっては、読み取り専用に、データ ソースかどうかを判断できます**SQLGetInfo** SQL_DATA_SOURCE_READ_ONLY 情報の種類とします。  
  
## <a name="statement"></a>ステートメントから削除してください。  
 *作成テーブル ステートメント*:: =  
  
 CREATE TABLE*ベース テーブル名*  
  
 (*列識別子のデータ型*[*、列識別子のデータ型*]...)  
  
> [!IMPORTANT]  
>  として、*データ型*で、*作成 table ステートメント*、アプリケーションは、によって返される結果セットの TYPE_NAME 列からデータ型を使用する必要があります**SQLGetTypeInfo**です。  
  
 *delete ステートメント検索*:: =  
  
 DELETE FROM*テーブル名*[場所*検索条件*]  
  
 *drop table ステートメント*:: =  
  
 DROP TABLE*ベース テーブル名*  
  
 *insert ステートメント*:: =  
  
 INSERT INTO*テーブル名*[(*列識別子*[、*列識別子*]...)]     値 (*挿入値*[、*挿入値*]...)  
  
 *select ステートメント*:: =  
  
 [すべて &#124; を選択します。DISTINCT]*選択リスト*  
  
 *テーブル参照一覧*  
  
 [場所*検索条件*]  
  
 [*order by*]  
  
 *ステートメント*:: =*作成 table ステートメント*  
  
 &#124; です。*delete ステートメントの検索*  
  
 &#124; です。*drop table ステートメント*  
  
 &#124; です。*insert ステートメント*  
  
 &#124; です。*select ステートメント*  
  
 &#124; です。*update ステートメントの検索*  
  
 *update ステートメントの検索*  
  
 更新*テーブル名*  
  
 設定*列識別子*= {*式*&#124; です。NULL}  
  
 [、*列識別子*= {*式*&#124; です。NULL}].  
  
 [場所*検索条件*]  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL ステートメントで使用される要素](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [データ型のサポート](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [パラメーターのデータ型](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [パラメーター マーカー](../../../odbc/reference/appendixes/parameter-markers.md)
