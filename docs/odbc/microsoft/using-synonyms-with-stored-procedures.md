---
title: "とのシノニムを使用してストアド プロシージャ |Microsoft ドキュメント"
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
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 46ad4937f804e5557d153ff94dd9c6ab559c9f81
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-synonyms-with-stored-procedures"></a>ストアド プロシージャでのシノニムの使用
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle バージョン 2.0 および 2.5 用の Microsoft ODBC Driver は、ストアド プロシージャを呼び出し元の Oracle 場合シノニムにできません。 シノニムは、テーブルなどの他の Oracle データベース オブジェクトで使用する場合に期待どおりに動作します。
