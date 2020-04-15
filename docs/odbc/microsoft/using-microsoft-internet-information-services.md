---
title: インターネット インフォメーション サービスの使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c71babf933c2615e6c2464696c1023ccaf53dd7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282469"
---
# <a name="using-microsoft-internet-information-services"></a>Microsoft インターネット インフォメーション サービスの使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 IIS スクリプト内から接続が困難な場合 (特に ORA-12641 エラーが発生した場合) は、次の行を Sqlnet.ora ファイルに追加します。  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 これにより、セキュア ネットワーク サービスが無効になり、匿名認証を使用して接続できるようになります。
