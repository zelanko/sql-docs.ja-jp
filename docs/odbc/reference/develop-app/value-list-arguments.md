---
title: リストの引数の値 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a971da68a8f2a35df8fa513e68d1eba127e9c430
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208551"
---
# <a name="value-list-arguments"></a>値リストの引数
リスト引数の値は、照合に使用する値のコンマ区切りの一覧で構成されます。 ODBC カタログ関数の 1 つの値リストの引数がある: *TableType*引数**SQLTables**します。 設定*TableType* null ポインターには、場合と同じ値の一覧のすべての可能なメンバーを列挙する、SQL_ALL_TABLE_TYPES に設定されています。 この引数は、SQL_ATTR_METADATA_ID ステートメント属性の影響を受けません。 詳細については、次を参照してください。、 [SQLTables](../../../odbc/reference/syntax/sqltables-function.md)関数の説明。
