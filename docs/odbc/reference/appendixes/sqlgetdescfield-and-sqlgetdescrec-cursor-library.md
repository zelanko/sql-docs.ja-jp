---
title: SQLGetDescフィールドと SQLGetDescRec (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49ceea6b6180e1b51f2f103f74412c3e2b4cbe02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307833"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField および SQLGetDescRec (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLGetDescField**関数と**SQLGetDescRec**関数の使用について説明します。 これらの関数の一般的な情報については、「 [SQLGetDesc フィールド関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)と[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)」を参照してください。  
  
 カーソル ライブラリは、ブックマーク列のメタデータを返すために**SQLGetDescRec**を実行します。 カーソル ライブラリは、SQL_DESC_NULLABLE SQL_DESC_SCALE SQL_DESC_PRECISION SQL_DESC_OCTET_LENGTH SQL_DESC_DATETIME_INTERVAL_CODE SQL_DESC_TYPE SQL_DESC_NAME **SQLGetDescRec**によって返されるのと同じフィールドを返す**SQLGetDescフィールド**を実行します。 一貫性を保つには **、sqlGetDescField**もSQL_DESC_UNNAMEDを返します。  
  
 カーソル ライブラリは、ブックマーク列のバインドに設定されている次のフィールドの値を返すために呼び出されたときに**SQLGetDescField**を実行します: SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR、およびSQL_DESC_LENGTH。  
  
 カーソル ライブラリは、SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_BIND_TYPE、SQL_DESC_ROW_ARRAY_SIZE、またはSQL_DESC_ROW_STATUS_PTRフィールドの値を返すために呼び出されたときに**SQLGetDescField**を実行します。 これらのフィールドは、ブックマーク行だけでなく、任意の行に対して返すことができます。  
  
 アプリケーションが**SQLGetDescField**を呼び出して、前述のフィールド以外のフィールドの値を返す場合、カーソル ライブラリは、ドライバーに呼び出しを渡します。
