---
title: ODBC 接続のテスト |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8de19af2b50a58eef22ec074a308f86717278a48
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303113"
---
# <a name="testing-the-odbc-connection"></a>ODBC の接続のテスト
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 7.x および Oracle8 RDBMS サーバーへの ODBC アクセスのトラブルシューティングを行う場合、基になる SQL*Net および Oracle プロトコル・アダプターが正しくインストールされていることを確認する必要があります。 これを行うには、Oracle 提供のユーティリティ Nettest.exe を Orawin\Bin ディレクトリで使用します。  
  
 Nettest は、Oracle クライアントの一部であるインストール済みの SQL*Net ソフトウェアのみを使用して、選択したサーバーにログオンしようとする単純なユーティリティです。 このユーティリティは、ログイン名、パスワード、および TNS 接続文字列を要求します。 Oracle クライアントが正しくインストールされている場合、ユーティリティは "Ping 成功" と表示されます。 ログインが失敗した場合は、データベース管理者に相談する必要があります。
