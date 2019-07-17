---
title: 検索ステートメントの構築 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8f24fe59da1377ea42900a8f1f0b89eb97125f3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019167"
---
# <a name="constructing-searched-statements"></a>検索ステートメントの構築
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 位置指定更新のサポートを delete ステートメントは、カーソル ライブラリを構築、検索された**更新**または**削除**位置指定のステートメントからのステートメント。 呼び出しをサポートする**SQLGetData**カーソル ライブラリを構築、検索データのブロックに**選択**結果を作成するステートメントは、データの現在の行を含むを設定します。 これらのステートメントの各、**場所**句で SQL_DESC_SEARCHABLE フィールド識別子 SQL_PRED_SEARCHABLE または SQL_PRED_BASIC から返されるバインドされた各列のキャッシュに格納されている値を列挙する**SQLColAttribute**します。  
  
> [!CAUTION]  
>  **場所**任意の行を識別する、別の行を特定または複数の行を識別する、現在の行を識別するために、カーソル ライブラリによって構築された句が失敗することができます。  
  
 位置指定の update または delete ステートメントを 1 つ以上の行に影響する場合、カーソル ライブラリをカーソルが配置されている、SQL_SUCCESS_WITH_INFO と SQLSTATE 01001 (カーソル操作の競合) を返しますの行のみの行の状態配列を更新します。 ステートメントで行が識別されない場合、カーソル ライブラリは行の状態配列を更新できませんし、SQL_SUCCESS_WITH_INFO と SQLSTATE 01001 (カーソル操作の競合) を返します。 アプリケーションが呼び出すことができます**SQLRowCount**更新または削除された行の数を決定します。  
  
 場合、**選択**の呼び出しにカーソルを配置するために使用する句**SQLGetData** 1 つ以上の行を識別します**SQLGetData**正しいデータを返すとは限りません。 すべての行を特定できない場合は**SQLGetData** sql_no_data が返されます。  
  
 アプリケーションは、次のガイドラインに準拠している場合、**場所**カーソル ライブラリによって構築された句がときにこれができない、データ ソースに重複が含まれている場合などを除き、現在の行を一意に識別する必要があります行。  
  
-   **行を一意に識別する列をバインドします。** バインドされた列が、行を一意に識別しない場合、**場所**カーソル ライブラリによって構築された句が 1 つ以上の行を識別する可能性があります。 位置指定更新または delete ステートメントでは、このような句には、複数の行を更新または削除することがあります。 呼び出しで**SQLGetData**、このような句が誤った行のデータを返すことがあります。 一意のキーですべての列をバインドには、各行は一意に識別されていることが保証されます。  
  
-   **切り捨ては行われませんが十分な大きさのデータ バッファーを割り当てます。** カーソル ライブラリのキャッシュが使用して結果セットにバインドされている行セットのバッファー内の値のコピーを**SQLBindCol**します。 これらのバッファーに配置されているときにデータが切り捨てられる場合、キャッシュにも切り捨てられます。 A**場所**切り捨てられた値から構築された句はデータ ソースの基になる行を正しく認識しない可能性があります。  
  
-   **C のバイナリ データのバッファーを null 以外の長さを指定します。** カーソル ライブラリが場合にのみ、そのキャッシュ内の長さのバッファーを割り当て、 *StrLen_or_IndPtr*引数**SQLBindCol**以外の場合します。 ときに、 *TargetType*引数は、SQL_C_BINARY、カーソル ライブラリを構築するバイナリ データの長さが必要です、**場所**データから句。 SQL_C_BINARY 列と、アプリケーションが長さのバッファーがないかどうか**SQLGetData**位置指定更新を実行、またはステートメントでは、カーソル ライブラリ返します SQL_ERROR と SQLSTATE SL014 を削除しようとしていますまたは (位置指定。要求が発行され、バッファーに格納されたすべての列数のフィールド)。  
  
-   **Null 許容の列の null 以外の長さのバッファーを指定します。** カーソル ライブラリが場合にのみ、そのキャッシュ内の長さのバッファーを割り当て、 *StrLen_or_IndPtr*引数**SQLBindCol**以外の場合します。 SQL_NULL_DATA で長さのバッファーであるため、カーソル ライブラリは、バッファーが指定されている長さのないの任意の列が null 非許容であると仮定します。 Null 許容列長の列が指定されていない場合、カーソル ライブラリを構築します、**場所**列のデータ値を使用する句。 この句が、行を正しく識別しません。
