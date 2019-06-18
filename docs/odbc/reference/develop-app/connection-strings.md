---
title: 接続文字列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7e52ec70e53608f1af48b4abcd2dd1edb4fc454
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042583"
---
# <a name="connection-strings"></a>接続文字列
接続文字列には、接続の確立に使用される情報が含まれています。 完全な接続文字列には、接続を確立するために必要なすべての情報が含まれています。 接続文字列は、一連のキーワード/値ペアのセミコロンで区切られたです。 (接続文字列の完全な構文を参照してください、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明です)。接続文字列は、によってを使用されます。  
  
-   **SQLDriverConnect**、接続文字列をユーザーとの対話を完了します。  
  
-   **SQLBrowseConnect**、データ ソースとやり取りしながら、接続文字列が完了します。  
  
 **SQLConnect**接続文字列を使用しませんを使用して**SQLConnect**には 3 つのキーワード/値ペアを持つ接続文字列を使用して接続するには似ています (データ ソース名と、必要に応じて、ユーザー ID とパスワード).
