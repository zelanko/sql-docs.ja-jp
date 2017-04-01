---
title: "SQL Server エラー ログの表示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server エラー ログの使い回し"
  - "SQL Server エラー ログの表示"
  - "エラー [SQL Server], ログ"
  - "SQL Server エラー ログ"
  - "SQL Server エラー ログの確認"
  - "ログ [SQL Server], SQL Server エラー ログ"
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# SQL Server エラー ログの表示
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを表示すると、バックアップ操作および復元操作、バッチ コマンド、その他のスクリプトやプロセスなどが正常に終了したことを確認できます。 これは、自動復旧メッセージ (特に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが停止してから再起動した場合)、カーネル メッセージ、またはその他のサーバー レベルのエラー メッセージを含んでいて、現在または潜在的に問題がある領域を検出するときに便利です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または任意のテキスト エディターを使用して表示します。 エラー ログの確認方法の詳細については、「[[ログ ファイルの表示] を開く](../Topic/Open%20Log%20File%20Viewer.md)」を参照してください。 エラー ログの既定の場所は、`Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` ファイルおよび `ERRORLOG.`*n* ファイルです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動するたびに、新しいエラー ログが作成されます。ただし、[sp_cycle_errorlog](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md) システム ストアド プロシージャを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再起動しなくてもエラー ログ ファイルを使い回すことができます。 一般的に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではログのバックアップが新しいものから 6 つ保持されます。最新のログ バックアップの拡張子は .1、2 番目に新しいログ バックアップの拡張子は .2 で、以降同様に続きます。 現在のエラー ログには拡張子がありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがオフラインになっている場合または起動できない場合も、そのインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを表示できます。 詳細については、「[オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)」を参照してください。  
  
  