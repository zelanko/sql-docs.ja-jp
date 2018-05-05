---
title: カーソル Attributes1 情報の種類のマッピング |Microsoft ドキュメント
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
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec986c2feea1b5c2ef64de87d64944ce0d184898
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>カーソル Attributes1 情報の種類のマッピング
ODBC 3 時にします。*x*アプリケーション呼び出し**SQLGetInfo** ODBC 2 で *.x* SQL_XXXX_CURSOR_ATTRIBUTES1 情報の種類のドライバー (、順方向専用の動的なキーセットのドライバー、または静的カーソル)、ドライバー マネージャーによって返されるビットの設定は、どのような ODBC 2 によって異なります。*x*ドライバーは対応する ODBC 2 を返します*。x*情報の種類。 ビットは、次の表に示すように設定されます。  
  
|内のビットします。<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|カーソルの種類|ODBC 2 です。*x*情報<br /><br /> 型|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|すべて|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE、SQL_CA1_BOOKMARK|動的、キーセット、静的|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE、SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|動的、キーセット、静的|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_DELETE、SQL_CA1_POSITIONED_UPDATE、SQL_CA1_SELECT_FOR_UPDATE|すべて|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE、SQL_CA1_POS_REFRESH、SQL_CA1_POS_BULK_ADD|動的、キーセット、静的|SQL_POS_OPERATIONS|
