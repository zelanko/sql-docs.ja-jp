---
title: ブックマークの種類 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f5c5a126ea220f055349ad00dc950281606ed4c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199245"
---
# <a name="bookmark-types"></a>ブックマークの種類
ODBC 3 のすべてのブックマーク *.x*は可変長のブックマーク。 これにより、プライマリ キーまたはブックマークとして使用するテーブルに関連付けられている一意のインデックス。 ブックマークも値を指定できます 32 ビット、ODBC 2 で使用されていたとします。*x*します。 カーソルでは、ODBC 3 は、ブックマークが使用されることを指定する *.x* SQL_UB_VARIABLE にアプリケーションが SQL_ATTR_USE_BOOKMARK ステートメント属性を設定します。 可変長のブックマークが自動的に使用します。  
  
 アプリケーションが呼び出すことができます**SQLColAttribute**で、 *FieldIdentifier*引数は、ブックマークの長さを取得する SQL_DESC_OCTET_LENGTH に設定します。 Long 型の値の可変長のブックマークを使用できる、ので 多数の行セットの行のブックマークを使用しない限り、列 0 にアプリケーションがバインドできません。  
  
 固定長のブックマークは、下位互換性のみサポートされます。 ODBC 2 場合。*x* 、ODBC 3 の操作アプリケーション *.x*ドライバー呼び出し**SQLSetStmtOption** SQL_USE_BOOKMARKS SQL_UB_ON に設定するドライバー マネージャーで SQL_UB_VARIABLE にマップされます. 可変長のブックマークを使用すると、場合でもの 32 ビットのみが設定されます。 ドライバーは、固定長のブックマークをサポートする場合は可変長のブックマークをサポートします。 場合、ODBC 3 *.x* ODBC 2 を使用するアプリケーション *。x*ドライバー呼び出し**SQLSetStmtAttr** SQL_UB_ON をドライバー マネージャーでをマップしている SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE に設定して 32 ビットの固定長のブックマークを使用します。 SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性は、32 ビットのブックマークをポイントする必要があります。 使用されるブックマークがブックマークとして主キーを使用する場合など、32 ビットよりも長い場合、カーソルは、32 ビット値を実際の値をマップする必要があります。 これらのハッシュ テーブルなど、構築できます、します。 ときに、ODBC 3 *.x* ODBC 2 を使用するアプリケーション *。x*ドライバー ブックマークをバインドする、バッファーの長さは 4 である必要があります。
