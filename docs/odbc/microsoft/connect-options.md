---
title: 接続オプション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25cfe2a897b0c312f91cd0c1e41ad6fa11725ab8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281312"
---
# <a name="connect-options"></a>接続のオプション
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 これらのオプションを使用すると、アプリケーション内のデータベース接続をカスタマイズできます。  
  
|接続オプション|Notes|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|SQL_AUTOCOMMIT_OFFを選択した場合、アプリケーションは[SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)を使用してトランザクションを明示的にコミットまたはロールバックする必要があります。|  
|SQL_ODBC_CURSORS|この接続属性は、ドライバー マネージャーで実装されます。|  
|SQL_OPT_TRACE|この接続属性は、ドライバー マネージャーで実装されます。|  
|SQL_OPT_TRACEFILE|この接続属性は、ドライバー マネージャーで実装されます。|  
|SQL_TRANSLATE_DLL|エラーを返します: "ドライバが機能しません。|  
|SQL_TRANSLATE_OPTION|変換 .dll に渡される 32 ビット値。|  
|SQL_TXN_ISOLATION|ドライバはSQL_TXN_READ_COMMITTEDのみを許可します。<br /><br /> 次の vParams はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|この ODBC 3.0 接続属性を使用すると、マイクロソフト コンポーネント サービス (または WINDOWS NT を使用している場合は MTS) によって調整された分散トランザクションで Oracle 用 ODBC ドライバーを使用できます。 *これは、vParam*引数としてトランザクションにインターフェイス ポインター *pITransaction*を提供します。|  
|SQL_ATTR_CONNECTION_DEAD|この読み取り専用 ODBC 3.5 接続属性を使用すると、Oracle サーバーへの接続が失敗したかどうかを判別できます。 取得のみ。設定できません。|
