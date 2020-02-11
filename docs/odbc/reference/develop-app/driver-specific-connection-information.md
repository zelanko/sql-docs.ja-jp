---
title: ドライバー固有の接続情報 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69f2c98678739a8b7879e152e13546f2bf9b9cc1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046933"
---
# <a name="driver-specific-connection-information"></a>ドライバー固有の接続情報
**SQLConnect**では、データソース名、ユーザー ID、およびパスワードを使用してデータソースに接続し、他のすべての接続情報をシステムに格納できることを前提としています。 これは多くの場合、そうではありません。 たとえば、サーバーにログオンするために1つのユーザー ID とパスワードが必要であり、DBMS にログオンするために別のユーザー ID とパスワードが必要になる場合があります。 **SQLConnect**は単一のユーザー id とパスワードを受け付けるため、 **SQLConnect**を使用する場合は、他のユーザー id とパスワードをシステム上のデータソース情報と共に保存する必要があります。 これはセキュリティ違反の可能性があるため、パスワードを暗号化しない限り回避する必要があります。  
  
 **SQLDriverConnect**を使用すると、ドライバーは接続文字列のキーワードと値のペアで任意の量の接続情報を定義できます。 たとえば、ドライバーがデータソース名、サーバーのユーザー ID とパスワード、および DBMS のユーザー ID とパスワードを必要とするとします。 常に XYZ Corp データソースを使用するカスタムプログラムでは、ユーザーに Id とパスワードの入力を求め、次の一連のキーワードと値のペア (*接続文字列)* を作成して、 **SQLDriverConnect**に渡すことができます。  
  
> [!NOTE]  
>  Windows 認証をサポートするデータソースプロバイダーに接続する場合は、接続文字列に`Trusted_Connection=yes`ユーザー ID とパスワードの情報ではなくを指定する必要があります。  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 **DSN** (データソース名) キーワードはデータソースに名前を指定し、 **UID**と**PWD**キーワードはサーバーのユーザー id とパスワードを指定します。また、 **uiddbms**と**PWDDBMS**キーワードは、DBMS のユーザー id とパスワードを指定します。 最後のセミコロンは省略可能であることに注意してください。 **SQLDriverConnect**は、この文字列を解析します。は、サーバーアドレスなどの追加の接続情報をシステムから取得するために、XYZ Corp データソース名を使用します。とは、指定されたユーザー Id とパスワードを使用して、サーバーと DBMS にログオンします。  
  
 **SQLDriverConnect**のキーワードと値のペアは、特定の構文規則に従う必要があります。 キーワードとその値には、 **[]{}()、;? を含めることはできません。= \*! @** 文字。 **DSN**キーワードの値は、空白のみで構成することはできません。また、先頭に空白を含めることはできません。 レジストリの文法により、キーワードとデータソース名に円記号 (\\) を含めることはできません。 キーワードと値のペアの等号を囲むスペースは使用できません。  
  
 **FILEDSN**キーワードを使用すると、 **SQLDriverConnect**を呼び出して、データソース情報を含むファイルの名前を指定できます (後の「[ファイルデータソースを使用した接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」を参照してください)。 **SAVEFILE**キーワードを使用すると、 **SQLDriverConnect**への呼び出しによって確立された接続のキーワードと値のペアが保存される、dsn ファイルの名前を指定できます。 ファイルデータソースの詳細については、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください。
