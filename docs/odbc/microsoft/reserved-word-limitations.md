---
description: 予約済みキーワードの制限事項
title: 予約語の制限 |Microsoft Docs
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
ms.openlocfilehash: 07917cbe056b38be42e4697fcef52935bae3efe3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449294"
---
# <a name="reserved-keyword-limitations"></a>予約済みキーワードの制限事項

SQL テーブルや関連オブジェクトの識別子として、ODBC の予約済みキーワードを使用することは避けてください。 予約済みキーワードを識別子として使用する必要がある場合に、奇数の場合は、 *バックティック* (') のペアで識別子を囲む必要があります。 *バックティック*のもう1つの名前は、*バッククォート*です。

予約済みキーワードの制限は、予約済みキーワードの短縮形にも適用されます。

ODBC の予約済みキーワードの一覧については、以下を参照してください。

- [ODBC の予約済みキーワード](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords)。

- *ODBC プログラマーズリファレンスガイド*については、「[付録 C: SQL 文法](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar)」を参照してください。

