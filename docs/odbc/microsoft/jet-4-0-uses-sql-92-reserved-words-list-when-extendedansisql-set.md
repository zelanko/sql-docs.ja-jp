---
title: Jet 4.0 では、ExtendedAnsiSQL_Setするときに SQL-92 予約語リストを使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6988e0da1ecb881e0f6e88e35b66f1a6284f9b7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299962"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 は ExtendedAnsiSQL_Set で SQL-92 の予約語リストを使用
拡張 AnsiSQL フラグがオンになっている場合、Jet 4.0 は SQL-92 予約語リストを使用します。 SQL-92 予約語を引用符で囲まれていないオブジェクト名として使用しようとすると、構文エラーが発生します。 ExtendedAnsiSQL フラグがオフの場合、新しい予約語は、以前と同じオブジェクト名として使用できます。
