---
title: 既定のデータソース |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 978362b7dfe92d1333f83be684f6326cf25dd69b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305993"
---
# <a name="default-data-source"></a>既定のデータ ソース
ドライバーは、既定のデータソースと呼ばれるデータソースを選択することがあります。ただし、アプリケーションで明示的に指定されていない場合があります。  
  
-   **SQLConnect**の呼び出しで、 *ServerName*引数が長さ0の文字列、null ポインター、または DEFAULT です。  
  
-   **SQLDriverConnect**の呼び出しで、 *inconnectionstring*は**dsn**= DEFAULT を指定するか、 **dsn**キーワードにシステム情報に含まれていないデータソースを指定します。  
  
 既定のデータソースを指定する方法はドライバーで定義されています。 これには管理操作が含まれる場合があり、ユーザーによって異なる場合があります。
