---
title: SQL Server のインプロセス固有の拡張 ADO.NET |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1d7e7dd5f40be276cf9cd3308d50f1c449aa343d
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37350900"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>ADO.NET に対する SQL Server インプロセス固有の拡張機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ADO.NET には、特にインプロセスで使用する、4 つの主要な拡張機能があります。 次のトピックでは、これらの拡張機能の詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SqlContext オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
 このクラスでは、インプロセスでマネージド コードを実行する SQL Server ルーチンの呼び出し元のコンテキストが抽象化され、他の拡張機能へのアクセスを提供します。  
  
 [SqlPipe オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
 このクラスには、表形式の結果とメッセージをクライアントに送信するためのルーチンが含まれています。  
  
 [SqlTriggerContext オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
 このクラスでは、トリガーを実行しているコンテキストに関する情報が提供されます。  
  
 [SqlDataRecord オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)  
 SqlDataRecord クラスは、1 行のデータとそのデータに関連するメタデータを表します。また、このクラスを使用すると、ストアド プロシージャからクライアントにカスタム結果セットを返すことができます。  
  
  
