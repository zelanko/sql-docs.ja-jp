---
title: ヘッダーレコード |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 372185966cc1644147feb2683177ae3a5b69e788
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300182"
---
# <a name="header-record"></a>ヘッダー レコード
ヘッダー・レコードのフィールドには、戻りコード、行カウント、状況レコードの数、実行されたステートメントのタイプなど、関数の実行に関する一般的な情報が含まれます。 関数がSQL_INVALID_HANDLEを返す場合を除き、ヘッダー レコードは常に作成されます。 ヘッダー レコードのフィールドの完全な一覧については[、SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明を参照してください。
