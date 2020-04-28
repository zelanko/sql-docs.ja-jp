---
title: SQLDriverConnect | を使用した接続Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6cd95364d8a5316a50d9f55616236a8677bf99e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299072"
---
# <a name="connecting-with-sqldriverconnect"></a>SQLDriverConnect による接続
**SQLDriverConnect**は、接続文字列を使用してデータソースに接続するために使用されます。 次の理由により、 **SQLConnect**の代わりに**SQLDriverConnect**が使用されます。  
  
-   アプリケーションでドライバー固有の接続情報を使用できるようにする場合は。  
  
-   ドライバーがユーザーに対して接続情報を要求する場合  
  
-   データソースを指定せずに接続する場合。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバー固有の接続情報](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [接続情報をユーザーに確認する](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [ファイル データ ソースを使用した接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [ドライバーに直接接続する](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
