---
title: とのシノニムを使用してストアド プロシージャ |Microsoft ドキュメント
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
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c662d5ee84f2d17159767be329f6a0817fc620b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-synonyms-with-stored-procedures"></a>ストアド プロシージャでのシノニムの使用
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle バージョン 2.0 および 2.5 用の Microsoft ODBC Driver は、ストアド プロシージャを呼び出し元の Oracle 場合シノニムにできません。 シノニムは、テーブルなどの他の Oracle データベース オブジェクトで使用する場合に期待どおりに動作します。
