---
title: SQL の文法 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26cf76200010edae7f85993ec33eb3722f35e94e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270495"
---
# <a name="sql-minimum-grammar"></a>SQL の最小限の文法
このセクションでは、ODBC ドライバーのサポートが必要な最低限の SQL 構文について説明します。 このセクションで説明する構文は、SQL 92 のエントリ レベルの構文のサブセットです。  
  
 アプリケーションでは、このセクションでは、構文のいずれかを使用でき、任意の ODBC に準拠したドライバーがその構文をサポートするを保証します。 このセクションではなく、sql-92 の他の機能がサポートされているかどうかを判断する、アプリケーションを呼び出す必要があります**SQLGetInfo** SQL_SQL_CONFORMANCE 情報の種類にします。 ドライバーは、任意の sql-92 準拠のレベルに準拠していない、場合でも、アプリケーションはこのセクションで説明する構文を使用できます。 その一方で、ドライバーは、SQL 92 レベルに準拠している場合、そのレベルに含まれるすべての構文をサポートします。 ここで説明されている最小限の文法最下位の sql-92 準拠レベルの純粋なサブセットであるため、このセクションに、構文を含めます。 かどうかをより高度な機能はサポートされて (あれば) 呼び出すことによって判断できるアプリケーションでは、サポートされている SQL 92 レベルがわかると**SQLGetInfo**とその機能に対応する個々 の情報の種類。  
  
 読み取り専用データ ソースでのみ動作するドライバーが、データの変更を処理するこのセクションに含まれる文法の一部をサポートしていません。 アプリケーションを調べるかどうか、データ ソースは読み取り専用呼び出して**SQLGetInfo** SQL_DATA_SOURCE_READ_ONLY 情報の種類にします。  
  
## <a name="statement"></a>ステートメントから削除してください。  
 *create table ステートメント*:: =  
  
 CREATE TABLE *base-table-name*  
  
 (*列識別子のデータ型*[*、列識別子のデータ型*]...)  
  
> [!IMPORTANT]  
>  として、*データ型*で、 *create table ステートメント*、アプリケーションがによって返される結果セットの TYPE_NAME 列からデータ型を使用する必要があります**SQLGetTypeInfo**します。  
  
 *delete ステートメント検索*:: =  
  
 DELETE FROM *table-name* [WHERE *search-condition*]  
  
 *drop-テーブル-ステートメント*:: =  
  
 DROP TABLE *base-table-name*  
  
 *insert ステートメント*:: =  
  
 INSERT INTO*テーブル名*[( *列識別子* [、 *列識別子*]...)]     値 (*挿入値*[、*挿入値*]...)  
  
 *select ステートメント*:: =  
  
 [すべて &#124; を選択します。DISTINCT]*選択リスト*  
  
 FROM *table-reference-list*  
  
 [WHERE *search-condition*]  
  
 [*order by*]  
  
 *ステートメント*:: = *create table ステートメント*  
  
 &#124; です。*delete ステートメントの検索*  
  
 &#124; です。*drop table ステートメント*  
  
 &#124; です。*insert ステートメント*  
  
 &#124; です。*select ステートメント*  
  
 &#124; です。*update ステートメントの検索*  
  
 *update-statement-searched*  
  
 UPDATE*テーブル名*  
  
 設定*列識別子*= {*式*&#124; です。NULL}  
  
 [、*列識別子*= {*式*&#124; です。NULL}].  
  
 [WHERE *search-condition*]  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL ステートメントで使用される要素](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [データ型のサポート](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [パラメーターのデータ型](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [パラメーター マーカー](../../../odbc/reference/appendixes/parameter-markers.md)
