---
title: 既定のデータ ソース |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305993"
---
# <a name="default-data-source"></a>既定のデータ ソース
ドライバーは、アプリケーションが明示的に指定しない場合には、既定のデータ ソースと呼ばれるデータ ソースを選択できます。  
  
-   *引数が*長さ 0 の文字列、null ポインタ、またはデフォルトである**SQLConnect**の呼び出しで。  
  
-   **SQLDriverConnect**の呼び出しでは *、InConnectionString*は**DSN**=DEFAULT を指定するか、DSN**キーワードで**システム情報に含まれていないデータ ソースを指定します。  
  
 既定のデータ ソースの指定方法は、ドライバーで定義されます。 これには管理上の操作が含まれる場合があり、ユーザーによって異なる場合があります。
