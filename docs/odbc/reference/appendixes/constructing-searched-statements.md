---
title: 検索ステートメントの作成 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8b9a27aa9fc84aadc6659993de3e12e269631d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284742"
---
# <a name="constructing-searched-statements"></a>検索ステートメントの構築
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 位置指定更新および削除ステートメントをサポートするために、カーソル・ライブラリーは、位置指定ステートメントから検索された**UPDATE**ステートメントまたは**DELETE**ステートメントを作成します。 データ ブロック内の**SQLGetData**の呼び出しをサポートするために、カーソル ライブラリは、検索された**SELECT**ステートメントを構築して、現在のデータ行を含む結果セットを作成します。 これらの各ステートメントでは、 **WHERE**句は **、SQLColAttribute**のSQL_DESC_SEARCHABLE フィールド識別子のSQL_PRED_SEARCHABLEまたはSQL_PRED_BASICを返すバインドされた各列のキャッシュに格納されている値を列挙します。  
  
> [!CAUTION]  
>  現在の行を識別するためにカーソル ライブラリによって作成された**WHERE**句は、行の識別、別の行の識別、または複数行の識別に失敗する可能性があります。  
  
 位置指定更新または削除ステートメントが複数の行に影響を与える場合、カーソル・ライブラリーはカーソルが位置付けられている行についてのみ行状況配列を更新し、SQL_SUCCESS_WITH_INFOおよび SQLSTATE 01001 (カーソル操作の競合) を戻します。 ステートメントが行を識別しない場合、カーソル・ライブラリーは行状況配列を更新せず、SQL_SUCCESS_WITH_INFOおよび SQLSTATE 01001 (カーソル操作の競合) を戻します。 アプリケーションは **、SQLRowCount**を呼び出して、更新または削除された行の数を決定できます。  
  
 **SQLGetData**への呼び出しのカーソルの位置を指定するために使用される**SELECT**句が複数の行を識別する場合 **、SQLGetData**は正しいデータを返す保証はありません。 行が識別されない**場合は**、SQL_NO_DATA返します。  
  
 アプリケーションが次のガイドラインに準拠している場合、カーソル ライブラリによって作成される**WHERE**句は、データ ソースに重複する行が含まれている場合など、これが不可能な場合を除き、現在の行を一意に識別する必要があります。  
  
-   **行を一意に識別する列をバインドします。** バインドされた列が行を一意に識別しない場合、カーソル ライブラリによって作成される**WHERE**句は複数の行を識別する可能性があります。 位置指定更新ステートメントまたは削除ステートメントでは、このような句によって複数の行が更新または削除される場合があります。 **SQLGetData**の呼び出しでは、このような句は、ドライバーが間違った行のデータを返す可能性があります。 一意キーですべての列をバインドすると、各行が一意に識別されます。  
  
-   **切り捨てが発生しないほど大きなデータ バッファを割り当てます。** カーソル ライブラリのキャッシュは **、SQLBindCol**を使用して結果セットにバインドされた行セット バッファー内の値のコピーです。 これらのバッファーにデータを格納するときに切り捨てられると、キャッシュ内でも切り捨てられます。 切り捨てられた値から作成された**WHERE**句は、データ ソースの基になる行を正しく識別できない場合があります。  
  
-   **2 進 C データの非 NULL 長バッファーを指定します。** カーソル ライブラリは **、SQLBindCol**の*StrLen_or_IndPtr*引数が null 以外の場合にのみ、そのキャッシュに長さのバッファーを割り当てます。 引数*TargetType*がSQL_C_BINARY場合、カーソル ライブラリは、データから**WHERE**句を構築するためにバイナリ データの長さを必要とします。 SQL_C_BINARY列に長さバッファーがなく、アプリケーションが**SQLGetData**を呼び出すか、または位置指定更新ステートメントまたは削除ステートメントを実行しようとすると、カーソル・ライブラリーは SQL_ERROR および SQLSTATE SL014 (位置指定要求が発行され、すべての列カウント・フィールドがバッファーに入れられていない) を戻します。  
  
-   **NULL 許容列に NULL 以外の長さのバッファーを指定します。** カーソル ライブラリは **、SQLBindCol**の*StrLen_or_IndPtr*引数が null 以外の場合にのみ、そのキャッシュに長さのバッファーを割り当てます。 SQL_NULL_DATAは長さバッファーに保管されるため、カーソル・ライブラリーは、長さバッファーが指定されていない列は null 非許容であると想定します。 NULL 許容列に長さ列が指定されていない場合、カーソル・ライブラリーは、その列のデータ値を使用する**WHERE**節を作成します。 この句は、行を正しく識別しません。
