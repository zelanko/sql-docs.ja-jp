---
title: "リスト引数の値 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15604e317105982c5011b31096934e32bea98e11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="value-list-arguments"></a>値リストの引数
リスト引数の値は、照合に使用する値をコンマ区切りの一覧で構成されます。 ODBC カタログ関数で 1 つの値リストの引数がある: *TableType*引数**SQLTables**です。 設定*TableType* null ポインターには、場合と同じ値の一覧のすべての可能なメンバーを列挙する SQL_ALL_TABLE_TYPES に設定されています。 この引数は SQL_ATTR_METADATA_ID ステートメント属性の影響を受けません。 詳細については、次を参照してください。、 [SQLTables](../../../odbc/reference/syntax/sqltables-function.md)関数の説明。
