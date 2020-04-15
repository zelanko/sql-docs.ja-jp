---
title: 値リストの引数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd655bd745c3bb06923e047d4134b286cf64703e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306743"
---
# <a name="value-list-arguments"></a>値リストの引数
値リスト引数は、マッチングに使用するコンマ区切り値のリストで構成されます。 ODBC カタログ関数には、値リスト引数が 1 つだけ*TableType*存在**します**。 *TableType*を null ポインターに設定すると、値リストのすべての可能なメンバーを列挙するSQL_ALL_TABLE_TYPESに設定されている場合と同じです。 この引数は、SQL_ATTR_METADATA_IDステートメント属性の影響を受けません。 詳細については[、SQLTables](../../../odbc/reference/syntax/sqltables-function.md)関数の説明を参照してください。
