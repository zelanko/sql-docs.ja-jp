---
title: 値リストの引数 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306743"
---
# <a name="value-list-arguments"></a>値リストの引数
値リストの引数は、照合に使用するコンマ区切り値のリストで構成されます。 ODBC カタログ関数には、値リストの引数が1つだけあります。 **Sqltables**の*TableType*引数です。 *TableType*を null ポインターに設定することは SQL_ALL_TABLE_TYPES に設定されている場合と同じです。これにより、値リストのすべての可能なメンバーが列挙されます。 この引数は、SQL_ATTR_METADATA_ID statement 属性の影響を受けません。 詳細については、 [Sqltables](../../../odbc/reference/syntax/sqltables-function.md)関数の説明を参照してください。
