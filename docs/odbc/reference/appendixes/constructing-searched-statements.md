---
title: ステートメントを構築する検索 |Microsoft ドキュメント
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
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f75e27da3b912e59b55cd6e53ec3b6af0412b866
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="constructing-searched-statements"></a>ステートメントを検索の構築
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 位置指定更新のサポートを delete ステートメントは、カーソル ライブラリを構築、検索**更新**または**削除**位置指定のステートメントからのステートメント。 呼び出しをサポートする**SQLGetData**でデータのブロック、カーソル ライブラリは、構築、検索**選択**データの現在の行を含む結果を作成するステートメントを設定します。 これらのステートメントの各、**場所**句またはを返す SQL_PRED_SEARCHABLE SQL_PRED_BASIC SQL_DESC_SEARCHABLE フィールド識別子内のバインドされた各列のキャッシュに格納されている値を列挙する**SQLColAttribute**です。  
  
> [!CAUTION]  
>  **場所**を任意の行を識別する、別の行を特定または複数の行を識別する、現在の行を識別する、カーソル ライブラリで構築された句が失敗します。  
  
 位置指定更新または削除ステートメントは、複数の行に影響する場合、カーソル ライブラリは、行の状態の配列のみ行をカーソルが配置されているし、返す SQL_SUCCESS_WITH_INFO と SQLSTATE 01001 (カーソル操作 conflict) を更新します。 ステートメントがすべての行を特定できない場合は、カーソル ライブラリは、行の状態配列は更新されませんし、SQL_SUCCESS_WITH_INFO と SQLSTATE 01001 (カーソル操作 conflict) を返します。 アプリケーションが呼び出すことができます**SQLRowCount**を更新または削除された行の数を決定します。  
  
 場合、**選択**位置にカーソルを呼び出すのために使用される句**SQLGetData** 1 つ以上の行を識別**SQLGetData**を正しいデータを返すとは限りません。 すべての行を特定できない場合は**SQLGetData** SQL_NO_DATA が返されます。  
  
 アプリケーションは、次のガイドラインに準拠している場合、**場所**カーソル ライブラリで構築された句は、ときにこれができない、データ ソースに重複が含まれている場合などを除き、現在の行を一意に識別する必要があります行です。  
  
-   **行を一意に識別する列をバインドします。** バインドされた列が、行を一意に識別しない場合、**場所**カーソル ライブラリで構築された句が 1 つ以上の行を識別する可能性があります。 位置指定更新または delete ステートメントでは、このような句に複数の行を更新または削除することがあります。 呼び出しで**SQLGetData**、このような句が正しくない行のデータを返すことがあります。 一意のキーのすべての列をバインド各行は一意に識別されていることを保証します。  
  
-   **切り捨ては行われませんするのに十分な大きさデータ バッファーを割り当てます。** カーソル ライブラリのキャッシュを使用して結果セットにバインドされている行セットのバッファー内の値のコピーである**SQLBindCol**です。 これらのバッファーに配置されているときにデータが切り捨てられた場合、キャッシュにも切り捨てられます。 A**場所**切り捨てられた値から構築された句がデータ ソースの基になる行を正しく認識しない可能性があります。  
  
-   **C のバイナリ データのバッファーを null 以外の長さを指定します。** カーソル ライブラリが場合にのみ、そのキャッシュの長バッファーを割り当て、 *StrLen_or_IndPtr*引数**SQLBindCol**以外の場合します。 ときに、 *TargetType*引数は、SQL_C_BINARY、カーソル ライブラリを構築するバイナリ データの長さが必要です、**場所**データから句。 SQL_C_BINARY 列およびアプリケーションの呼び出しの長バッファーがないかどうか**SQLGetData**または位置指定更新を実行または delete ステートメントをカーソル ライブラリを返し SQL_ERROR SQLSTATE SL014 しよう (位置指定要求が発行されがバッファー内のすべての列数のフィールド)。  
  
-   **Null 許容列の null 以外の長バッファーを指定します。** カーソル ライブラリが場合にのみ、そのキャッシュの長バッファーを割り当て、 *StrLen_or_IndPtr*引数**SQLBindCol**以外の場合します。 SQL_NULL_DATA が長さのバッファーに格納されているため、カーソル ライブラリは、バッファーが指定されている長さのない任意の列が null 非許容であると仮定します。 Null 許容列長の列が指定されていない場合、カーソル ライブラリを構築、**場所**列のデータ値を使用する句。 この句が行を正しく識別しません。
