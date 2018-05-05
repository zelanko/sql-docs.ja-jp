---
title: カーソル機能を判断する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3974fb30a9151cdcf681a106ddcf3073b63f66b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="determining-cursor-capabilities"></a>カーソル機能を判断します。
次の 4 つのオプション**SQLGetInfo**カーソルの種類がサポートされており、機能について説明します。  
  
-   SQL_CURSOR_SENSITIVITY です。 カーソルが別のカーソルによって行われた変更に影響するかどうかを示します。  
  
-   SQL_SCROLL_OPTIONS です。 サポートされているカーソルの種類 (順方向専用、静的、キーセット ドリブン、動的、または混合) を一覧表示します。 すべてのデータ ソースには、順方向専用カーソルをサポートする必要があります。  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_CURSOR_ATTRIBUTES1 (カーソルの種類) によって異なります。 スクロール可能なカーソルでサポートされるフェッチの種類を一覧表示します。 フェッチの型に対応して、戻り値のビット**SQLFetchScroll**です。  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 または SQL_STATIC_CURSOR_ATTRIBUTES2 (カーソルの種類) によって異なります。 静的カーソルとキーセット ドリブン カーソルは、独自の更新、削除、および挿入を検出できるかどうかを示します。  
  
 アプリケーションは、実行時にカーソル機能を呼び出すことによって判断できます**SQLGetInfo**でこれらのオプションです。 これは一般的に、汎用アプリケーションによって実行します。 カーソル機能もを決定できるアプリケーションの開発とハード コーディングされた、使用中に、アプリケーションにします。 これは、垂直方向およびカスタム アプリケーションで一般的に実行されますが、ODBC カーソル ライブラリなど、クライアント側カーソルの実装を使用する汎用アプリケーションによって行うこともできます。
