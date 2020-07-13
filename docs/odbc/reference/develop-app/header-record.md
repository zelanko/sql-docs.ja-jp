---
title: ヘッダーレコード |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300182"
---
# <a name="header-record"></a>ヘッダー レコード
ヘッダーレコード内のフィールドには、関数の実行に関する一般的な情報が含まれています。これには、リターンコード、行数、状態レコードの数、実行されたステートメントの種類などが含まれます。 関数が SQL_INVALID_HANDLE を返さない限り、ヘッダーレコードは常に作成されます。 ヘッダーレコード内のフィールドの完全な一覧については、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明を参照してください。
