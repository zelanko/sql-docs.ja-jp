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
ms.openlocfilehash: 02509ddb6a986ebb7796d80aca10c6f18cde6e69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939704"
---
# <a name="testing-the-odbc-connection"></a>ODBC の接続のテスト
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 Oracle 6.x および Oracle8 RDBMS サーバーへの ODBC アクセスのトラブルシューティングを行うときに、基になる SQL * Net および Oracle プロトコルアダプターが正しくインストールされていることを確認する必要がある場合があります。 これを行うには、Orawin\Bin ディレクトリにある、Oracle によって提供されるユーティリティの Nettest .exe を使用します。  
  
 Nettest は、Oracle クライアントの一部であるインストール済みの SQL * Net ソフトウェアのみを使用して、選択したサーバーへのログオンを試行する単純なユーティリティです。 ユーティリティは、ログイン名、パスワード、および TNS 接続文字列を要求します。 Oracle クライアントが正しくインストールされている場合は、ユーティリティによって "Ping に成功しました" と表示されます。 ログインに失敗した場合は、データベース管理者に相談する必要があります。
