---
title: カーソルの種類および同時実行の組み合わせ |Microsoft ドキュメント
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
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d594474abe27b028b74219a921a12a4737148536
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cursor-type-and-concurrency-combinations"></a>カーソルの種類および同時実行の組み合わせ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 カーソルの種類は、ユーザーに提供されたカーソルの機能を制御します。 同時実行オプションは、更新し、結果セットのロック動作を制御します。  
  
|カーソルの種類|同時実行 (有効な値)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup>を参照してください[のキーセット ドリブン カーソルの使用に関する制限](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md)です。  
  
 <sup>[2]</sup> SQL_CONCUR_LOCK は SQL_AUTOCOMMIT 接続オプションが SQL_AUTOCOMMIT_OFF に設定されている場合にのみサポートされます。  
  
## <a name="see-also"></a>参照  
 [接続のオプション](../../odbc/microsoft/connect-options.md)
