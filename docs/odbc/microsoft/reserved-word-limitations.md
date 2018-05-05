---
title: Word の制限に予約されています |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 010546fe5d0d987443fb4deebc4409cb5e867085
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="reserved-keyword-limitations"></a>予約済みキーワードの制限事項

SQL テーブルまたは関連するオブジェクト内で識別子として任意の ODBC の予約済みキーワードを使用しないでください。 ペアに識別子を囲む必要があります、奇数のケースでは、識別子として、予約済みキーワードを使用する必要がありますが発生した場合、*バックティック*(')。 別の名前*バックティック*は*後ろ向き引用符*です。

予約済みキーワードの制限は、予約済みキーワードの略式フォームにも適用されます。

ODBC の予約済みキーワードの一覧で入手できます。

- [ODBC の予約済みキーワード](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords)です。

- *ODBC プログラマ リファレンス ガイド*を参照してください[付録 c: SQL 文法](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar)です。

