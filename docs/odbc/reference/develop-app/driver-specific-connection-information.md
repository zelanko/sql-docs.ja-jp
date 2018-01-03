---
title: "ドライバー固有の接続情報 |Microsoft ドキュメント"
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
- SQLConnect function [ODBC], driver-specific connection information
- connecting to driver [ODBC], SQLConnect
- SQLDriverConnect function [ODBC], driver specific connection information
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SQLConnect
- connecting to driver [ODBC], driver-specific information
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3352a0a31e6bb48be84d72a7da84eb3d7c6100c9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="driver-specific-connection-information"></a>ドライバー固有の接続情報
**SQLConnect**データ ソース名、ユーザー ID とパスワードがデータ ソースに接続するための十分なことと、システム上の他のすべての接続情報を格納できることを前提としています。 これは頻繁に当てはまりません。 たとえば、ドライバーは、1 人のユーザー ID とパスワード、サーバー、および別のユーザー ID とパスワードにログオンする DBMS にログオンする必要があります。 **SQLConnect** 1 人のユーザー ID とパスワードを受け入れるつまり他のユーザー ID とパスワードが場合、システム上のデータ ソース情報を格納する必要があります**SQLConnect**を使用します。 これは潜在的なセキュリティ侵害であり、パスワードが暗号化されていない限り避ける必要があります。  
  
 **SQLDriverConnect**接続文字列のキーワードと値のペアで接続情報の任意の大きさを定義するドライバーを使用します。 たとえば、ドライバーが必要です、データ ソース名、ユーザー ID とパスワード、サーバーと、ユーザー ID とパスワードの DBMS のとします。 常に"xyz"Corp データ ソースを使用するカスタム プログラム可能性があります Id とパスワードのユーザーの入力を求めるし、次のキーワードと値のペアのセットを構築または*接続文字列、*に渡す**SQLDriverConnect**:  
  
> [!NOTE]  
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する`Trusted_Connection=yes`接続文字列でユーザー ID とパスワード情報の代わりにします。  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 **DSN** (データ ソース名) のキーワード、データ ソースの名前、 **UID**と**PWD**キーワードは、ユーザー ID と、サーバーのパスワードを指定し、 **UIDDBMS**と**PWDDBMS**キーワードは、DBMS のユーザー ID とパスワードを指定します。 最後のセミコロンが省略可能なことに注意してください。 **SQLDriverConnect**この文字列を解析して以外の場合は"xyz"Corp データ ソース名を使用して、サーバーのアドレスなど、システムから追加の接続情報を取得する、DBMS が、指定されたユーザー Id とパスワードを使用して、サーバーにログオンします。  
  
 キーワードと値のペアで**SQLDriverConnect**特定構文規則に従う必要があります。 キーワードとその値を含めないで、 **{} ()、;?\*=! @**文字です。 値、 **DSN**キーワードは、空白のみ含めることはできませんし、先頭の空白を含めることはできません。 レジストリの文法のためのキーワードおよびデータ ソース名が円記号を含めることはできません (\\) 文字です。 スペースはキーワード/値ペア内の等号 (=) を使用できません。  
  
 **FILEDSN**キーワードへの呼び出しで使用することができます**SQLDriverConnect**をデータ ソースの情報を含むファイルの名前を指定する (を参照してください[接続を使用してファイル データ ソース](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)、このセクションで後述)。 **SAVEFILE**への呼び出しによって正常な接続のキーワードと値のペアが行われた .dsn ファイルの名前を指定するキーワードを使用できる**SQLDriverConnect**は保存されます。 ファイルのデータ ソースの詳細については、次を参照してください。、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明。
