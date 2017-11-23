---
title: "接続情報をユーザーに確認 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to data source [ODBC], SqlConnect
- connecting to driver [ODBC], prompting user for information
- connecting to driver [ODBC], SQLConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLConnect function [ODBC], prompting user for connection information
- connecting to data source [ODBC], prompting user for information
- prompting user for connection information [ODBC]
- SQLDriverConnect function [ODBC], prompting user for connection information
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dc8ca40adb6a70b56d9b91842fa1fd560fc50f8a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="prompting-the-user-for-connection-information"></a>接続情報をユーザーに確認
アプリケーションで使用する場合**SQLConnect**接続についてユーザーに確認する必要があるなど、ユーザー名とパスワードに行ってください自体です。 これにより、アプリケーションは、「ルック アンド フィール」を制御する、中にドライバー固有のコードを格納するアプリケーションが強制的に可能性があります。 これは、アプリケーションは、ドライバー固有の接続についてユーザーに確認する必要がある場合に発生します。 これは、汎用アプリケーション、アプリケーションが書き込まれるときに存在しないドライバーを含む、すべてのドライバーを使用するように設計されているため不可能の状況を表示します。  
  
 **SQLDriverConnect**接続情報を求めることができます。 たとえば、前に述べたカスタム プログラムに次の接続文字列を渡しますでした**SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 ドライバーは、ユーザー Id と次の図のように、パスワードの入力を求めるダイアログ ボックスを表示し、可能性があります。  
  
 ![ユーザー Id とパスワードの入力を求めるダイアログ ボックス](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 接続情報、ドライバーが要求できることは、ジェネリックおよび垂直方向のアプリケーションに特に便利です。 これらのアプリケーションがドライバーに固有の情報を含めることはできませんし、必要な情報のドライバーのプロンプトを持つ、アプリケーションからその情報を保持します。 これは、前の 2 つの例で表示します。 ドライバーに、アプリケーションがデータ ソース名のみを渡すと、アプリケーションは、ドライバー固有の情報が含まれていませんでしたされ、特定のドライバーにも関連付けられませんでした。 アプリケーションでは、ドライバーに完全な接続文字列が渡される、ときに、その文字列を解釈することが、ドライバーに関連付けるされました。  
  
 汎用アプリケーションは、さらにこの 1 つの手順を実行しであっても、データ ソースを指定可能性があります。 ときに**SQLDriverConnect**次のダイアログ ボックスに、ドライバー マネージャーが表示されます、空の接続文字列を受信します。  
  
 ![[データ ソース] ダイアログ ボックス](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 ユーザーは、データ ソースを選択し、ドライバー マネージャーがそのデータ ソースを指定する接続文字列を構築して、ドライバーに渡します。 ドライバーは、必要なその他の情報のユーザーを要求し、ことができます。  
  
 ドライバーが、ユーザーを要求する条件はによって制御されます、 *DriverCompletion*フラグ以外の場合は、常に確認する、必要に応じての確認、またはメッセージを表示せずにオプションがあります。 このフラグの詳細については、次を参照してください。、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明。
