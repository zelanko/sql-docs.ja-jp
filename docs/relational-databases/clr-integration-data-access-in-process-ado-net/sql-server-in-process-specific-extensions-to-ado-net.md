---
title: SQL Server のインプロセス固有の拡張 ADO.NET |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: b1ed0cf58c34506ce12dd04bf529a80d44a03d2d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951688"
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
  
  
