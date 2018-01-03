---
title: "ODBC の接続のテスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cffb08b48128500b37c6f55e37a848be19c266a8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="testing-the-odbc-connection"></a>ODBC の接続のテスト
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle ODBC アクセスのトラブルシューティングを行う 7.x と Oracle8 RDBMS サーバーで必要があることを確認する、基になる SQL * Net および Oracle プロトコルのアダプターが正しくインストールされています。 これを行うには、ユーティリティを使用して、Oracle が提供 Nettest.exe Orawin\Bin ディレクトリにします。  
  
 含む、Nettest がインストールされている SQL のみを使用して、選択したサーバーにログオンしようとする単純なユーティリティ * Net の Oracle クライアントの一部であるソフトウェアです。 ログイン名を求められたら、パスワード、および TNS 接続文字列。 Oracle クライアントが正しくインストールされている場合、単が表示されます「Ping 成功します」 ログインが成功しなかった場合は、データベース管理者に相談する必要があります。
