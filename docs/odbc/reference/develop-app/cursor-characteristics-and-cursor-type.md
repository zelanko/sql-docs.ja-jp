---
title: カーソルの特性とカーソルの種類 |Microsoft ドキュメント
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
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b73c8d966f0974b09b672e497238f122bf1b13da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912293"
---
# <a name="cursor-characteristics-and-cursor-type"></a>カーソルの特性とカーソルの種類
アプリケーションでは、(順方向専用、静的、キーセット ドリブンまたは動的) カーソルの種類を指定する代わりに、カーソルの特性を指定できます。 これを行うには、アプリケーションが選択されます (属性を設定して、SQL_ATTR_CURSOR_SCROLLABLE ステートメント) のカーソルのスクロール機能と感度 (属性を設定して、SQL_ATTR_CURSOR_SENSITIVITY ステートメント) のステートメントでカーソルを開く前に処理します。 ドライバーは、アプリケーションが要求した特性をする最も効率的に提供する、カーソルの種類を選択します。  
  
 ドライバーがこの一連の他のステートメント属性に、必要な変更を加え、アプリケーション設定のステートメント属性 SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_SCROLLABLE、SQL_ATTR_CURSOR_SENSITIVITY、または SQL_ATTR_CURSOR_TYPE、されるたびに4 つの属性の値の一貫性を保持できるようにします。 その結果、アプリケーションでは、カーソルの特性を指定する場合、ドライバー属性を変更できるこの選択に基づく暗黙的な; カーソルの種類を示すアプリケーションでは、型を指定する場合、ドライバーは、選択した型の特性に一致するように他の属性のいずれかを変更できます。 これらのステートメント属性の詳細については、次を参照してください。、 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)関数の説明。  
  
 カーソルの種類とカーソル特性の両方を指定するステートメント属性を設定するアプリケーションには、そのドライバー、アプリケーションの要件を満たすに使用可能な最も効率的な方法ではないカーソルを取得するリスクが実行されます。  
  
 ステートメント属性の暗黙的な設定は、ドライバーの定義が、これらの規則に従う必要があります。  
  
-   順方向専用カーソルがスクロール可能な; ことはありません。SQL_ATTR_CURSOR_SCROLLABLE での定義を参照して[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)です。  
  
-   Insensitive カーソルは更新できません (とそのため、同時実行は読み取り専用) です。これは、ISO SQL 標準で insensitive のカーソルの定義に基づきます。  
  
 そのため、ステートメント属性の暗黙的な設定は、次の表で説明されている場合に発生します。  
  
|アプリケーションでは、属性を設定するには|その他の属性が暗黙的に設定します。|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY SQL_INSENSITIVE にします。|  
|したり SQL_CONCUR_LOCK、SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES SQL_ATTR_CONCURRENCY|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED または SQL_SENSITIVE、ドライバーで定義されています。 決してに設定できます SQL_INSENSITIVE、insensitive カーソルは、常に読み取り専用であるためです。|  
|SQL_ATTR_CURSOR_SCROLLABLE が SQL_NONSCROLLABLE に|SQL_CURSOR_FORWARD_ONLY に SQL_ATTR_CURSOR_TYPE|  
|SQL_ATTR_CURSOR_SCROLLABLE が SQL_SCROLLABLE に|SQL_CURSOR_STATIC、SQL_CURSOR_KEYSET_DRIVEN、または、ドライバーで指定したとおり、SQL_CURSOR_DYNAMIC SQL_ATTR_CURSOR_TYPE です。 SQL_CURSOR_FORWARD_ONLY には設定されません。|  
|SQL_ATTR_CURSOR_SENSITIVITY が SQL_INSENSITIVE に|SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY です。<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC にします。|  
|SQL_ATTR_CURSOR_SENSITIVITY が SQL_SENSITIVE に|SQL_CONCUR_LOCK、SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES、ドライバーで指定したとおりに SQL_ATTR_CONCURRENCY です。 SQL_CONCUR_READ_ONLY には設定されません。<br /><br /> SQL_CURSOR_FORWARD_ONLY、SQL_CURSOR_STATIC、SQL_CURSOR_KEYSET_DRIVEN、または、ドライバーで指定したとおり、SQL_CURSOR_DYNAMIC SQL_ATTR_CURSOR_TYPE です。|  
|SQL_ATTR_CURSOR_SENSITIVITY が SQL_UNSPECIFIED に|SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY、SQL_CONCUR_LOCK、SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES、ドライバーで指定されたまたはします。<br /><br /> SQL_CURSOR_FORWARD_ONLY、SQL_CURSOR_STATIC、SQL_CURSOR_KEYSET_DRIVEN、または、ドライバーで指定したとおり、SQL_CURSOR_DYNAMIC SQL_ATTR_CURSOR_TYPE です。|  
|SQL_CURSOR_DYNAMIC に SQL_ATTR_CURSOR_TYPE|SQL_SCROLLABLE に SQL_ATTR_SCROLLABLE です。<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE にします。 (ただし SQL_ATTR_CONCURRENCY が SQL_CONCUR_READ_ONLY と等しくない場合にのみです。 更新可能な動的カーソルは常に独自のトランザクションで行われた変更に影響します。)|  
|SQL_CURSOR_FORWARD_ONLY に SQL_ATTR_CURSOR_TYPE|SQL_ATTR_CURSOR_SCROLLABLE を SQL_NONSCROLLABLE にします。|  
|SQL_CURSOR_KEYSET_DRIVEN に SQL_ATTR_CURSOR_TYPE|SQL_SCROLLABLE に SQL_ATTR_SCROLLABLE です。<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED または SQL_SENSITIVE (ドライバーの定義済み条件に従って、SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY ではない場合)。|  
|SQL_CURSOR_STATIC に SQL_ATTR_CURSOR_TYPE|SQL_SCROLLABLE に SQL_ATTR_SCROLLABLE です。<br /><br /> SQL_ATTR_SENSITIVITY SQL_INSENSITIVE (SQL_ATTR_CONCURRENCY が SQL_CONCUR_READ_ONLY の場合) にします。<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED または SQL_SENSITIVE (SQL_ATTR_CONCURRENCY が SQL_CONCUR_READ_ONLY でない場合)。|
