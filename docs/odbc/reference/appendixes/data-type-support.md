---
title: データ型のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 820e48a17e397bc9046c8ca431677074e69b8cb2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905837"
---
# <a name="data-type-support"></a>データ型のサポート
ODBC ドライバーは、SQL_CHAR、SQL_VARCHAR の少なくとも 1 つをサポートする必要があります。 その他のデータ型のサポートについては、ドライバーのまたはデータ ソースの sql-92 準拠レベルによって決まります。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**ドライバーによってサポートされるデータ型を決定します。  
  
 データ型の詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。
