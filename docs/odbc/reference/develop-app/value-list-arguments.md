---
title: リスト引数の値 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47ef5564ae56f04877aa33b4ffb0f1644aa4d605
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="value-list-arguments"></a>値リストの引数
リスト引数の値は、照合に使用する値をコンマ区切りの一覧で構成されます。 ODBC カタログ関数で 1 つの値リストの引数がある: *TableType*引数**SQLTables**です。 設定*TableType* null ポインターには、場合と同じ値の一覧のすべての可能なメンバーを列挙する SQL_ALL_TABLE_TYPES に設定されています。 この引数は SQL_ATTR_METADATA_ID ステートメント属性の影響を受けません。 詳細については、次を参照してください。、 [SQLTables](../../../odbc/reference/syntax/sqltables-function.md)関数の説明。
