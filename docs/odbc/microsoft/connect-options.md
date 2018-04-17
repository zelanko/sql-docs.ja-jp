---
title: 接続のオプション |Microsoft ドキュメント
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
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6bbd2e6840a1f1a4f83bcadaba31139b27102418
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connect-options"></a>接続のオプション
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 これらのオプションには、アプリケーション内でのデータベース接続のカスタマイズができるようにします。  
  
|接続オプション|注|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|アプリケーションのコミットまたはでトランザクションをロールバックする必要があります明示的に SQL_AUTOCOMMIT_OFF 場合は、 [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)です。|  
|SQL_ODBC_CURSORS|この接続属性には、ドライバー マネージャーでは実装されます。|  
|SQL_OPT_TRACE|この接続属性には、ドライバー マネージャーでは実装されます。|  
|SQL_OPT_TRACEFILE|この接続属性には、ドライバー マネージャーでは実装されます。|  
|SQL_TRANSLATE_DLL|エラーが返されます"ドライバー対応していない"。|  
|SQL_TRANSLATE_OPTION|32 ビット値は、翻訳 .dll に渡されます。|  
|SQL_TXN_ISOLATION|ドライバーは、SQL_TXN_READ_COMMITTED のみを使用します。<br /><br /> 次の vParams はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|この ODBC 3.0 接続属性では、Oracle の Microsoft コンポーネント サービス (または Windows NT を使用している場合は MTS) によってコーディネートされる分散トランザクションで ODBC ドライバーを使用することができます。 インターフェイス ポインターを提供*pITransaction*としてトランザクションを*vParam*引数。|  
|SQL_ATTR_CONNECTION_DEAD|この読み取り専用の ODBC 3.5 接続属性では、Oracle サーバーへの接続が失敗したかどうかを判断することができます。 取得のみです。設定できません。|
