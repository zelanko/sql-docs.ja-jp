---
title: データ型のサポート |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d58bae6de18ca4d7f67258e8d3a859d3ce0a6aa1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-support"></a>データ型のサポート
ODBC ドライバーは、SQL_CHAR、SQL_VARCHAR の少なくとも 1 つをサポートする必要があります。 その他のデータ型のサポートについては、ドライバーのまたはデータ ソースの sql-92 準拠レベルによって決まります。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**ドライバーによってサポートされるデータ型を決定します。  
  
 データ型の詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。
