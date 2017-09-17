---
title: "SQLDriverConnect による接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7bdfbf03fb4e67fcd0bc88ecf9212e3bb9cd7773
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-with-sqldriverconnect"></a>SQLDriverConnect による接続
**SQLDriverConnect**接続文字列を使用してデータ ソースに接続するために使用します。 **SQLDriverConnect**の代わりに使用される**SQLConnect**次の理由。  
  
-   ドライバー固有の接続情報を使用してアプリケーションをできるようにします。  
  
-   ドライバーがユーザーに対して接続情報を要求する場合  
  
-   データ ソースを指定しなくても接続します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバー固有の接続情報](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [接続情報をユーザーに確認](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [ファイルのデータ ソースを使用して接続します。](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [ドライバーに直接接続します。](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
