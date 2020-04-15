---
title: ドライバ固有の接続情報 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConnect function [ODBC], driver-specific connection information
- connecting to driver [ODBC], SQLConnect
- SQLDriverConnect function [ODBC], driver specific connection information
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SQLConnect
- connecting to driver [ODBC], driver-specific information
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16c8c5fc4fd3ac63aa3613b41e530446dffec118
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305793"
---
# <a name="driver-specific-connection-information"></a>ドライバー固有の接続情報
**SQLConnect**は、データ・ソース名、ユーザー ID、およびパスワードがデータ・ソースに接続するのに十分であり、他のすべての接続情報をシステムに保管できることを前提としています。 これは多くの場合は当てはまりません。 たとえば、あるドライバがサーバーにログオンするために 1 つのユーザー ID とパスワード、および DBMS にログオンするために別のユーザー ID とパスワードが必要な場合があります。 **SQLConnect**は単一のユーザー ID とパスワードを受け入れるため **、SQLConnect**を使用する場合は、他のユーザー ID とパスワードをシステム上のデータ ソース情報と共に格納する必要があります。 これはセキュリティ違反の可能性があり、パスワードが暗号化されていない限り避けるべきです。  
  
 **SQLDriverConnect**を使用すると、ドライバーは、接続文字列のキーワードと値のペアで接続情報の任意の量を定義できます。 たとえば、ドライバーが、データ ソース名、サーバーのユーザー ID とパスワード、および DBMS のユーザー ID とパスワードを必要とします。 常に XYZ Corp データ ソースを使用するカスタム プログラムは、ユーザーに ID とパスワードを要求し、次のキーワードと値のペアのセット、つまり*接続文字列*を作成して**SQLDriverConnect**に渡す場合があります。  
  
> [!NOTE]  
>  Windows 認証をサポートするデータ ソース プロバイダに接続する場合は、接続文字列`Trusted_Connection=yes`でユーザー ID とパスワード情報の代わりに指定する必要があります。  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 **DSN** (データ・ソース名) キーワードはデータ・ソースを指定し **、UID**キーワードと**PWD**キーワードはサーバーのユーザー ID とパスワードを指定し **、UIDDBMS**および**PWDDBMS**キーワードは DBMS のユーザー ID とパスワードを指定します。 最後のセミコロンは省略可能です。 この文字列**を解析します**。は、XYZ Corp データ ソース名を使用して、サーバー アドレスなどの追加の接続情報をシステムから取得します。をクリックし、指定されたユーザ ID とパスワードを使用してサーバおよび DBMS にログオンします。  
  
 **SQL ドライバ接続**のキーワード値ペアは、特定の構文規則に従う必要があります。 キーワードとその値には **[] ()、;?{}\*=!@** 文字。 **DSN**キーワードの値は、ブランクのみで構成することはできません。 レジストリ文法のため、キーワードとデータ ソース名には円記号 (\\) 文字を含めることはできません。 キーワードと値のペアでは、等号の前後にスペースを入れることはできません。  
  
 **FILEDSN**キーワードは **、SQLDriverConnect**の呼び出しで、データ ソース情報を含むファイルの名前を指定するために使用できます (このセクションの後半の[「ファイル データ ソースを使用して接続する](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」を参照してください)。 **SAVEFILE**キーワードを使用して **、SQLDriverConnect**の呼び出しによって行われた接続のキーワードと値のペアを保存する .dsn ファイルの名前を指定できます。 ファイル データ ソースの詳細については[、SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください。
