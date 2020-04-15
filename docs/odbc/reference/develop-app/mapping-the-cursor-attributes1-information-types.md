---
title: カーソル属性のマッピング1 情報タイプ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d70cf0a93a6c6160faeb0afe991b2adfff11b8f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301045"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Cursor Attributes1 の情報の種類のマッピング
ODBC 3 のとき。*x*アプリケーションは、ODBC 2 *.x*ドライバで**SQLGetInfo**を呼び出し、SQL_XXXX_CURSOR_ATTRIBUTES1情報の種類 (動的、前方専用、キーセット ドライバ、または静的カーソル) を使用して、ドライバ マネージャが返すビットの設定は ODBC 2 の内容によって異なります。*x*ドライバは対応する ODBC 2 に対して返します。*x*情報型。 ビットは、次の表に示すように設定されます。  
  
|ビットイン<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|カーソルの種類|ODBC 2.*x*情報<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|動的,キーセットドライバ,静的|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_LOCK_NO_CHANGE|動的,キーセットドライバ,静的|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_REFRESHSQL_CA1_POS_BULK_ADDSQL_CA1_POS_DELETESQL_CA1_POS_POSITION|動的,キーセットドライバ,静的|SQL_POS_OPERATIONS|
