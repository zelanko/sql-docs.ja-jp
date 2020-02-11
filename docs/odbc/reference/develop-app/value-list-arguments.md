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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 646d2724489140080a673f31e22429cc7ca39d4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022098"
---
# <a name="value-list-arguments"></a>値リストの引数
値リストの引数は、照合に使用するコンマ区切り値のリストで構成されます。 ODBC カタログ関数には、値リストの引数が1つだけあります。 **Sqltables**の*TableType*引数です。 *TableType*を null ポインターに設定することは SQL_ALL_TABLE_TYPES に設定されている場合と同じです。これにより、値リストのすべての可能なメンバーが列挙されます。 この引数は、SQL_ATTR_METADATA_ID statement 属性の影響を受けません。 詳細については、 [Sqltables](../../../odbc/reference/syntax/sqltables-function.md)関数の説明を参照してください。
