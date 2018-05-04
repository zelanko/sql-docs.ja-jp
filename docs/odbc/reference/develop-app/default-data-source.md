---
title: 既定のデータ ソース |Microsoft ドキュメント
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
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3aeb96caca91b681ec7d2a9d34548ba6bac1147f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="default-data-source"></a>既定のデータ ソース
ドライバーは、ここで、アプリケーションで明示的に指定されない 1 つ特定の場合で、既定のデータ ソースと呼ばれる、データ ソースを選択できます。  
  
-   呼び出しで**SQLConnect**場所、 *ServerName*引数が長さ 0 の文字列、null ポインター、または DEFAULT です。  
  
-   呼び出しで**SQLDriverConnect**場所*InConnectionString*いずれかを示す**DSN**= 既定値または指定、 **DSN**キーワード、システム情報に含まれていないデータ ソースです。  
  
 これはドライバーで定義されている既定のデータ ソースを指定する方法です。 これにより、管理操作を伴う場合がありますされ、ユーザーに依存している可能性があります。
