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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8fb016ac7597617b119834e20ffd9e12bd648dc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076847"
---
# <a name="default-data-source"></a>既定のデータ ソース
ドライバーは、既定のデータソースと呼ばれるデータソースを選択することがあります。ただし、アプリケーションで明示的に指定されていない場合があります。  
  
-   **SQLConnect**の呼び出しで、 *ServerName*引数が長さ0の文字列、null ポインター、または DEFAULT です。  
  
-   **SQLDriverConnect**の呼び出しで、 *inconnectionstring*は**dsn**= DEFAULT を指定するか、 **dsn**キーワードにシステム情報に含まれていないデータソースを指定します。  
  
 既定のデータソースを指定する方法はドライバーで定義されています。 これには管理操作が含まれる場合があり、ユーザーによって異なる場合があります。
