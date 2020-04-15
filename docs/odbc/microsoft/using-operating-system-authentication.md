---
title: オペレーティング システム認証の使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6520202bdbc31baf1156531457cb70a98656e88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292842"
---
# <a name="using-operating-system-authentication"></a>オペレーティング システムの認証の使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle オペレーティング システム認証は、基盤となるオペレーティング システムに依存して、データベース アカウントへのアクセスを制御します。 このタイプのログインを使用する場合、ユーザーはパスワードを入力する必要はありません。  
  
 この機能を利用するには、ユーザー ID として "/" を指定し、接続時に[SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) [、SQLConnect、](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)または[SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)のいずれかの接続 API を使用してパスワードを指定しないでください。  
  
 Oracle データベースは、SQL*Net 認証サービスを使用して、ログオンしているユーザーを認証します。 このサービスは、ユーザーが SQLPlus を使用して Oracle にログインしている場合に適しています。ただし、ログインしているユーザーがインターネット インフォメーション サービスなどのサービスの場合、認証は失敗します。 これは SQL\*ネット認証の既知の制限事項であり、次のエラーが生成されます: "[Microsoft][Oracle 用 ODBC ドライバー][Oracle]ORA-12641: TNS:認証サービスの初期化に失敗しました。  
  
 この問題は、Sqlnet.ora ファイルを編集することで解決できます。 この構成ファイルは、通常、Oracle ホーム ディレクトリのネットワーク\管理サブディレクトリに格納されます。 次の行を Sqlnet.ora に追加します。  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
