---
title: C データ型をブックマーク |Microsoft ドキュメント
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
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43a9c02694e121eb653d70693587d5728931f747
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bookmark-c-data-type"></a>ブックマークの C データ型
ブックマークの C データ型には、ブックマークを取得するアプリケーションができます。 ブックマーク C 型は可変長です。 使用可能なブックマークの値を取得する場合のみ使用されます。他のデータ型に変換する必要がありますされません。 アプリケーションの取得と設定のいずれかの結果の列 0 からブックマーク**SQLBulkOperations** (の SQL_ADD の操作)、 **SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**です。 詳細については、次を参照してください。[ブックマーク](../../../odbc/reference/develop-app/bookmarks-odbc.md)です。  
  
 次の表の値を一覧表示*CType* SQL からブックマーク C データ型のブックマーク C データ型、およびこのデータの定義を実装する ODBC C データ型を入力します。H.  
  
> [!NOTE]  
>  SQL_C_BOOKMARK データ型は廃止されました。 ODBC 3*.x*アプリケーション SQL_C_BOOKMARK を使用しないでください。 ODBC 3*.x*ドライバーは、ODBC 2 を使用する場合にのみ、SQL_C_BOOKMARK をサポートする必要があります*。x*それを使用するアプリケーション。 ドライバー マネージャーでは、ODBC 2 で動作するアプリケーション、SQL_C_VARBOOKMARK を SQL_C_BOOKMARK にマップします。*x*ドライバー。  
  
|C 型識別子|ODBC C の typedef|C 型|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(非推奨)。|ブックマーク|符号なし long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
