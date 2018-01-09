---
title: "SQL Server インプロセス固有の拡張 ado.net |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c8f08c7432fc179d5f85992d2aab7dc8df86815e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>ADO.NET に対する SQL Server インプロセス固有の拡張機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]次の 4 つ主な機能拡張機能がある ADO.NET には具体的には、プロセスで使用します。 次のトピックでは、これらの拡張機能の詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SqlContext オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
 このクラスでは、インプロセスでマネージ コードを実行する SQL Server ルーチンの呼び出し元のコンテキストが抽象化され、他の拡張機能へのアクセスを提供します。  
  
 [SqlPipe オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
 このクラスには、表形式の結果とメッセージをクライアントに送信するためのルーチンが含まれています。  
  
 [SqlTriggerContext オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
 このクラスでは、トリガーを実行しているコンテキストに関する情報が提供されます。  
  
 [SqlDataRecord オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)  
 SqlDataRecord クラスは、1 行のデータとそのデータに関連するメタデータを表します。また、このクラスを使用すると、ストアド プロシージャからクライアントにカスタム結果セットを返すことができます。  
  
  
