---
title: Bookmark C データ型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6264b245667d4378e126151616bd1e936000fcd0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712596"
---
# <a name="bookmark-c-data-type"></a>Bookmark C データ型
ブックマークの C データ型では、ブックマークを取得するアプリケーション。 ブックマーク C 型は可変長; できるブックマークの値を取得する場合のみ使用されます。他のデータ型に変換する必要がありますされません。 アプリケーションの取得と設定のいずれかから結果の列 0 ブックマーク**SQLBulkOperations** SQL_ADD の操作)、(で**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**します。 詳細については、次を参照してください。[ブックマーク](../../../odbc/reference/develop-app/bookmarks-odbc.md)します。  
  
 次の表の値*CType*ブックマーク C データ型では、ブックマーク C データ型、およびこのデータの定義を実装する ODBC C データ型を SQL から入力します。H.  
  
> [!NOTE]  
>  SQL_C_BOOKMARK のデータ型は非推奨とされました。 ODBC 3 *.x*アプリケーションは SQL_C_BOOKMARK を使用しないでください。 ODBC 3 *.x*ドライバーは ODBC 2 を使用する場合にのみ、SQL_C_BOOKMARK をサポートする必要があります *。x*を使用するアプリケーション。 ドライバー マネージャーは、ODBC 2 で動作するアプリケーションに SQL_C_BOOKMARK SQL_C_VARBOOKMARK をマップします。*x*ドライバー。  
  
|C 型識別子|ODBC C の typedef|C 型|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(非推奨)|ブックマーク|符号なし long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
