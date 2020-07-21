---
title: ストアドプロシージャでのシノニムの使用 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d3758aeb954427f333c5a22298d6675c04acdb5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292762"
---
# <a name="using-synonyms-with-stored-procedures"></a>ストアド プロシージャでのシノニムの使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 Microsoft ODBC Driver for Oracle バージョン2.0 および2.5 では、Oracle ストアドプロシージャを呼び出すときにシノニムはサポートされません。 シノニムは、テーブルなどの他の Oracle データベースオブジェクトと共に使用すると、想定どおりに動作します。
