---
title: "オペレーティング システムの認証を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da8b5adf34774f2ee6f7b224d7ab18f20a4dd09e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="using-operating-system-authentication"></a>オペレーティング システムの認証を使用します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle オペレーティング システムの認証は、データベース アカウントへのアクセスを制御する基になるオペレーティング システムに依存します。 この種類のログインを使用する場合、ユーザーはパスワードを入力する必要があります。  
  
 この機能を利用するには指定「/」は、ユーザー ID と Api の次の接続のいずれかを使用して接続するときにパスワードを指定しないと: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md)、 [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)、または[SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)です。  
  
 Oracle データベースに使用して SQL * Net の認証サービスにログオンしているユーザーを認証します。 このサービスの動作に SQLPlus; を通じて Oracle ユーザーがログインしている場合は、ただし、ログイン ユーザーは、インターネット インフォメーション サービスなどのサービスが、認証に失敗します。 これは、SQL の既知の制限\*Net 認証し、次のエラーを生成:"[Microsoft] [ODBC driver for Oracle] [Oracle] か 12641: TNS:authentication サービスが初期化に失敗しました"。  
  
 この問題を修正するには、Sqlnet.ora ファイルを編集します。 この構成ファイルは通常、Network\Admin、Oracle ホーム ディレクトリのサブディレクトリに格納されています。 Sqlnet.ora に次の行を追加します。  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
