---
title: 予約語の制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf536e06556e6b2e7b27f220d09a51f91b44d23c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304010"
---
# <a name="reserved-keyword-limitations"></a>予約キーワードの制限

ODBC 予約キーワードは、SQL テーブルまたは関連オブジェクトの識別子として使用しないでください。 予約キーワードを識別子として使用する必要がある場合、奇数のケースが発生した場合は、識別子を*バックティック*(') のペアで囲む必要があります。 *バックティック*の別の名前は *、引用の戻る*です。

予約キーワードの制限は、予約キーワードの任意の短縮形にも適用されます。

ODBC 予約キーワードのリストは、次のページで入手できます。

- [ODBC 予約キーワード](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords):

- ODBC*プログラマ リファレンス ガイド*の[「付録 C: SQL 文法](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar)」を参照してください。

