---
title: ユーザーに接続情報の入力を求める |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b0f120a1076f14f5e67d506e52a446e0a3d4713
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282085"
---
# <a name="prompting-the-user-for-connection-information"></a>接続情報をユーザーに確認する
アプリケーションが**SQLConnect**を使用し、ユーザー名やパスワードなどの接続情報をユーザーに求める必要がある場合は、それ自体で行う必要があります。 これにより、アプリケーションは"ルック アンド フィール" を制御できますが、アプリケーションにドライバー固有のコードを含める必要があります。 これは、アプリケーションがドライバー固有の接続情報をユーザーに求める必要がある場合に発生します。 これは、アプリケーションの作成時に存在しないドライバーを含む、すべてのドライバーで動作するように設計された汎用アプリケーションでは不可能な状況を示します。  
  
 **接続**情報を求めるメッセージを表示できます。 たとえば、前述のカスタム プログラムは、次の接続文字列を**SQLDriverConnect**に渡すことができます。  
  
```  
DSN=XYZ Corp;  
```  
  
 ドライバーは、次の図のように、ユーザー ID とパスワードを入力するダイアログ ボックスを表示する可能性があります。  
  
 ![ユーザー ID とパスワードの入力を求めるダイアログ ボックス](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 ドライバーが接続情報を要求できることは、汎用および垂直アプリケーションに特に便利です。 これらのアプリケーションには、ドライバー固有の情報を含めないようにする必要があり、必要な情報をドライバープロンプトで表示すると、その情報はアプリケーションから除外されます。 これは、前の 2 つの例で示されています。 アプリケーションがドライバにデータ ソース名のみを渡した場合、アプリケーションにはドライバ固有の情報が含まれなかったため、特定のドライバに関連付けられてはなりません。 アプリケーションが完全な接続文字列をドライバーに渡すと、その文字列を解釈できるドライバーに結び付けられていた。  
  
 汎用アプリケーションでは、この 1 つの手順を実行し、データ ソースを指定しない場合もあります。 **SQLDriverConnect**が空の接続文字列を受信すると、ドライバー マネージャーは、次のダイアログ ボックスを表示します。  
  
 ![[データ ソースの選択] ダイアログ ボックス](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 ユーザーがデータ ソースを選択すると、ドライバー マネージャーは、そのデータ ソースを指定する接続文字列を構築し、ドライバーに渡します。 ドライバーは、必要な追加情報をユーザーに求めることができます。  
  
 ドライバーがユーザーに求める条件は *、DriverCompletion*フラグによって制御されます。常にプロンプトを表示したり、必要に応じてプロンプトを表示したり、プロンプトを表示しないオプションがあります。 このフラグの詳細については[、SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください。
