---
title: 接続を確立する |Microsoft ドキュメント
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
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establising a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establising a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80de9f41bf4c535f7d9daa34b7b14d0377ab2383
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="establishing-a-connection"></a>接続を確立します。
環境と接続ハンドルを割り当てると、接続属性を設定、アプリケーションがデータ ソースまたはドライバーに接続できるようにします。 これを行うアプリケーションで使用して 3 つの異なる関数があります: **SQLConnect** (コア インターフェイスへの準拠レベル)、 **SQLDriverConnect** (Core)、および**SQLBrowseConnect**(レベル 1)。 別のシナリオで使用する、3 つに設計されています。 接続すると、前に、アプリケーションを判断できますではサポートされているこれらの関数、 **ConnectFunctions**キーワードによって返される**SQLDrivers**です。  
  
> [!NOTE]  
>  一部のドライバーは、サポートされるアクティブな接続の数を制限します。 アプリケーションが呼び出す**SQLGetInfo**特定のドライバーをサポートしているアクティブな接続の数を決定する SQL_MAX_DRIVER_CONNECTIONS オプションを使用します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [既定のデータ ソース](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [SQLConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [接続文字列](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [SQLDriverConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [SQLBrowseConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
