---
title: "作成して、スレッドの終了 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62950dba2174baac8e3bc34c60f268e07304fa5a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-terminating-threads"></a>作成して、スレッドの終了
ODBC を使用するマルチ スレッド アプリケーションは、Microsoft® Visual C++® ランタイム ライブラリ関数を呼び出す必要があります**_beginthread**と**_endthread** (または**_beginthreadex**と**_endthreadex**) を作成し、ODBC ドライバー マネージャーを呼び出してスレッドを終了します。 アプリケーションが Microsoft Windows NT® 関数を呼び出す場合**CreateThread**と**EndThread**代わりに、メモリ リークは、ドライバー マネージャーと一部の ODBC ドライバーは、C ランタイムを呼び出すために発生する可能性は関数呼び出しによって作成されたスレッド上で動作しません**CreateThread**です。 詳細については、Microsoft Windows® ドキュメントを参照してください。
