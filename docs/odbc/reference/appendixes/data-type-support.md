---
title: "データ型のサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 147e940dcd37b452e1fe05b3a39f6b184c810397
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-support"></a>データ型のサポート
ODBC ドライバーは、SQL_CHAR、SQL_VARCHAR の少なくとも 1 つをサポートする必要があります。 その他のデータ型のサポートについては、ドライバーのまたはデータ ソースの sql-92 準拠レベルによって決まります。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**ドライバーによってサポートされるデータ型を決定します。  
  
 データ型の詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。

