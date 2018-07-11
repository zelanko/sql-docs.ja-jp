---
title: マルチ スレッド アプリケーション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35768c262c3a2c0512a23049d6988eadfcb978d8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426861"
---
# <a name="multithreaded-applications"></a>マルチスレッド アプリケーション
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはマルチスレッド ドライバーです。 マルチスレッド アプリケーションは、非同期呼び出しを使用して複数の ODBC 呼び出しを処理するための代替手段として作成されます。 あるスレッドが同期 ODBC 呼び出しを実行すると、その呼び出しへの応答を待機するために最初のスレッドがブロックされている間に、他のスレッドの処理を実行できます。 このモデルは、ネットワーク トラフィックなどのオーバーヘッドが取り除かれるので、非同期呼び出しを実行するよりも効率的です。また、ODBC 関数を繰り返し呼び出して SQL_STILL_EXECUTING が返されるかどうかをテストするよりも効率的です。  
  
 それでも、非同期モードは、依然として効果的な処理方法です。 マルチスレッド モデルによるパフォーマンスの向上は、非同期アプリケーションを書き直すほどのものではありません。 ユーザーが DB-Library 非同期モデルを使用する DB-Library アプリケーションを ODBC アプリケーションに変換する場合は、ODBC 非同期モデルに変換する方が容易です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client ODBC ドライバー アプリケーションの作成](creating-a-driver-application.md)  
  
  
