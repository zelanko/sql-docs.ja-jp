---
title: ブックマークの種類 |Microsoft ドキュメント
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
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9a8f6fb698e55e2a5de623bfa4252468ba655ee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bookmark-types"></a>ブックマークの種類
ODBC 3 のすべてのブックマーク *.x*可変長のブックマークがします。 これにより、プライマリ キーまたはブックマークとして使用するテーブルに関連付けられている一意のインデックス。 ブックマークも使用できますが、32 ビット値 ODBC 2 で使用されていたとします。*x*です。 カーソルでは、ODBC 3、ブックマークが使用されることを指定する *.x* SQL_UB_VARIABLE にアプリケーションが SQL_ATTR_USE_BOOKMARK ステートメント属性を設定します。 可変長のブックマークが自動的に使用します。  
  
 アプリケーションが呼び出すことができます**SQLColAttribute**で、 *FieldIdentifier*引数が、ブックマークの長さを取得する SQL_DESC_OCTET_LENGTH に設定します。 可変長のブックマークには、long 型の値を使用できますがため、ブックマークは、行セット内の行の多くを使用しない限り、列 0 にアプリケーションはバインドできません。  
  
 固定長のブックマークは、旧バージョンとの互換性のみサポートされます。 ODBC 2 場合。*x* ODBC 3 作業アプリケーション *.x*ドライバー呼び出し**SQLSetStmtOption** SQL_USE_BOOKMARKS SQL_UB_ON に設定には SQL_UB_VARIABLE をドライバー マネージャーで、マップ. 可変長ブックマークが使用される場合でもの 32 ビットのみが生成されます。 ドライバーは、固定長のブックマークをサポートする場合は、可変長のブックマークをサポートします。 場合、ODBC 3 *.x* ODBC 2 を使用するアプリケーション*。x*ドライバー呼び出し**SQLSetStmtAttr** SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE に設定には SQL_UB_ON をドライバー マネージャーで、マップし、32 ビットの固定長ブックマークを使用します。 SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性は、32 ビットのブックマークをポイントする必要があります。 使用されるブックマークをブックマークとして主キーを使用する場合などの 32 ビットよりも長い場合、カーソルは、32 ビット値に、実際の値をマップする必要があります。 でした、たとえば、ビルドする必要がそれらのハッシュ テーブルです。 ときに ODBC 3 *.x* ODBC 2 を使用するアプリケーション*。x*ドライバーのブックマークをバインドする、バッファーの長さは 4 である必要があります。
