---
title: 引数の値のチェック |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6c6e4de16c4a1a80be893acbc7a1993b375f2fee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298826"
---
# <a name="argument-value-checks"></a>引数の値のチェック
ドライバー マネージャーは、次の種類の引数をチェックします。 特に明記されていない限り、ドライバ マネージャは、引数の値にエラーがないかSQL_ERRORを返します。  
  
-   環境、接続、およびステートメントのハンドルは、通常、NULL ポインターにすることはできません。 ドライバー マネージャーは、null ハンドルが見つかったときにSQL_INVALID_HANDLEを返します。  
  
-   必要なポインター引数 **(SQLAllocHandle**の*出力HandlePtr*や**SQLSetCursorName**の*カーソル名*など) は NULL ポインターにできません。  
  
-   ドライバー固有の値をサポートしないオプション フラグは、有効な値である必要があります。 たとえば **、SQLSetPos**の*操作*は、SQL_POSITION、SQL_REFRESH、SQL_UPDATE、SQL_DELETE、またはSQL_ADDである必要があります。  
  
-   オプション フラグは、ドライバーでサポートされている ODBC のバージョンでサポートされている必要があります。 たとえば、ODBC 2.0 ドライバを呼び出すときに **、SQLGetInfo**の*情報型*をSQL_ASYNC_MODEすることはできません (ODBC 3.0 で導入)。  
  
-   列番号およびパラメーター番号は、関数に応じて、0 より大きいか、0 以上である必要があります。 ドライバーは、現在の結果セットまたは SQL ステートメントに基づいて、これらの引数の値の上限をチェックする必要があります。  
  
-   長さ/インジケーター引数とデータ・バッファー長引数には、適切な値が含まれている必要があります。 たとえば **、SQLColumns** (*NameLength3*) のテーブル名の長さを指定する引数は、SQL_NTSまたは 0 より大きい値である必要があります。*バッファー長は* **0**以上である必要があります。 ドライバーは、これらの引数を確認する必要があります。 たとえば *、NameLength3*がデータ ソース内のテーブル名の最大長以下であることを確認できます。
