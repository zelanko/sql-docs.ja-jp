---
title: SQLBrowseConnect による接続 |Microsoft ドキュメント
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
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6382b0a02963395008dd02c962c10479aa5f29d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connecting-with-sqlbrowseconnect"></a>SQLBrowseConnect による接続
**SQLBrowseConnect**と同様、 **SQLDriverConnect**、接続文字列を使用します。 使用して、ただし、 **SQLBrowseConnect**アプリケーションは実行時に完全な接続文字列を構築することができます。 この方法を使用すると、アプリケーションで次の 2 つのことを行えます。  
  
-   この情報は、それによって「ルック アンド フィール」に対する制御を維持を要求する、独自のダイアログ ボックスを作成します。  
  
-   特定のドライバーが使用できるデータ ソースをシステムから参照できます。これは複数の手順になる場合があります。 たとえば、ユーザーは最初にネットワークを介してサーバーを参照して、サーバーを選択します。次に、そのサーバーを介して、ドライバーがアクセスできるデータベースを参照するといった手順です。  
  
 アプリケーションの呼び出し**SQLBrowseConnect**と呼ばれる、接続文字列を渡すと、*要求の接続文字列を参照*ドライバーまたはデータ ソースを指定します。 ドライバーと呼ばれる接続文字列を返します、*結果の接続文字列を参照*キーワード、(キーワードは、不連続値のセットを受け入れる) 場合の可能な値を格納していると、わかりやすい名前。 アプリケーションがわかりやすい名前を含むダイアログ ボックスにビルドされ、値の入力を求めます。 これらの値から新しい参照の要求の接続文字列を構築し、これを別の呼び出しを使用してドライバーを返します**SQLBrowseConnect**です。  
  
 接続文字列は前後に渡されるため、ドライバーは、アプリケーションには、古いパスワードが返されるときに、新しい接続文字列を返すことによってブラウズのいくつかのレベルを提供できます。 たとえばを初めてアプリケーションを呼び出す**SQLBrowseConnect**ドライバーは、サーバー名のユーザー入力を求めるキーワードを返す場合があります。 アプリケーションでは、サーバー名を返します、ときに、ドライバーはデータベースのユーザー入力を求めるキーワードを返す場合があります。 アプリケーションには、データベース名が返された後、参照プロセスが完了しています。  
  
 毎回**SQLBrowseConnect**新しい参照の結果の接続文字列を返しますとしてそのリターン コード SQL_NEED_DATA が返されます。 これは、アプリケーションに通知、接続処理が完了していません。 まで**SQLBrowseConnect**を返し SQL_SUCCESS、接続が必要なデータの状態には使用できません、他の目的などの接続属性を設定します。 アプリケーションが呼び出すことでプロセスを参照する接続を終了できる**SQLDisconnect**です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [SQL Server の参照の例](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
