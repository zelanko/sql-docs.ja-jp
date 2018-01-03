---
title: "データ型のサポート |Microsoft ドキュメント"
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4885db2868e5baf301264d2b29a18831d02dcf26
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-support"></a>データ型のサポート
ODBC ドライバーは、SQL_CHAR、SQL_VARCHAR の少なくとも 1 つをサポートする必要があります。 その他のデータ型のサポートについては、ドライバーのまたはデータ ソースの sql-92 準拠レベルによって決まります。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**ドライバーによってサポートされるデータ型を決定します。  
  
 データ型の詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。
