---
title: ODBC 接続のテスト |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 543ab436ac7dca5e0d5965220cd90a798afb5ccf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633177"
---
# <a name="testing-the-odbc-connection"></a>ODBC の接続のテスト
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle ODBC へのアクセスのトラブルシューティングを行う 7.x、Oracle8 RDBMS サーバーことが考えられますことを確認するために必要な基になる SQL * Net および Oracle プロトコル アダプターが正しくインストールされています。 これを行うには、ユーティリティを使用して、Oracle が指定した Nettest.exe Orawin\Bin ディレクトリにします。  
  
 含む、Nettest がインストールされている SQL のみを使用して、選択したサーバーにログオンしようとする単純なユーティリティ * Net の Oracle クライアントの一部であるソフトウェア。 文字列は、求められたら、ログイン名、パスワード、および TNS から接続します。 「Ping に成功しました"が表示されます単に Oracle クライアントが正しくインストールされている場合 ログインに失敗した場合は、データベース管理者に相談する必要があります。
