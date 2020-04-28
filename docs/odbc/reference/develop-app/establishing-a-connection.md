---
title: 接続を確立する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establishing a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establishing a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f71190a8a2ca1dd8af0d28adb5531540fb1b57e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298702"
---
# <a name="establishing-a-connection"></a>接続の確立
環境ハンドルと接続ハンドルを割り当て、接続属性を設定すると、アプリケーションはデータソースまたはドライバーに接続する準備が整います。 アプリケーションでは、 **SQLConnect** (コアインターフェイス準拠レベル)、 **SQLDriverConnect** (Core)、および**SQLBrowseConnect** (レベル 1) という3つの異なる機能を使用できます。 3つはそれぞれ、異なるシナリオで使用するように設計されています。 接続する前に、アプリケーションでは、 **Sqldrivers**によって返される**connectfunctions**キーワードでサポートされている関数を特定できます。  
  
> [!NOTE]  
>  一部のドライバーでは、サポートするアクティブな接続の数が制限されています。 アプリケーションは、SQL_MAX_DRIVER_CONNECTIONS オプションを使用して**SQLGetInfo**を呼び出し、特定のドライバーがサポートするアクティブな接続の数を決定します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [既定のデータ ソース](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [SQLConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [接続文字列](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [SQLDriverConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [SQLBrowseConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
