---
title: SQL Server エージェント テーブル (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server Agent, system tables
- system tables [SQL Server], SQL Server Agent
ms.assetid: 6cb39bfd-079e-4be4-9c42-2fa234c65ce1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1bdab681e7946df0845193ebcd183e392e000c74
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794910"
---
# <a name="sql-server-agent-tables-transact-sql"></a>SQL Server エージェントのテーブル (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用される情報を格納するシステム テーブルについて説明します。 すべてのテーブルは、msdb データベースの dbo スキーマにです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [dbo.sysalerts](../../relational-databases/system-tables/dbo-sysalerts-transact-sql.md)  
 警告 1 件につき 1 行のデータを格納します。  
  
 [dbo.syscategories](../../relational-databases/system-tables/dbo-syscategories-transact-sql.md)  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、ジョブ、警告、オペレーターの分類に使用されるカテゴリを格納します。  
  
 [dbo.sysdownloadlist](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)  
 すべての対象サーバーに対するダウンロード命令のキューを格納します。  
  
 [dbo.sysjobactivity](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
 現在の情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブの利用状況と状態。  
  
 [dbo.sysjobhistory](../../relational-databases/system-tables/dbo-sysjobhistory-transact-sql.md)  
 スケジュールされたジョブの実行に関する情報を格納[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。  
  
 [dbo.sysjobs](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによる実行が予定されているジョブに関する情報を格納します。  
  
 [dbo.sysjobschedules](../../relational-databases/system-tables/dbo-sysjobschedules-transact-sql.md)  
 によって実行されるジョブのスケジュール情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント  
  
 [dbo.sysjobservers](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)  
 特定のジョブと 1 つ以上の対象サーバーとの関連付けまたはリレーションシップを格納します。  
  
 [dbo.sysjobsteps](../../relational-databases/system-tables/dbo-sysjobsteps-transact-sql.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって実行されるジョブ内の各ステップに関する情報を格納します。  
  
 [dbo.sysjobstepslogs](../../relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql.md)  
 ジョブ ステップ ログに関する情報を格納します。  
  
 [dbo.sysnotifications](../../relational-databases/system-tables/dbo-sysnotifications-transact-sql.md)  
 通知ごとに 1 行のデータを格納します。  
  
 [dbo.sysoperators](../../relational-databases/system-tables/dbo-sysoperators-transact-sql.md)  
 ごとに 1 つの行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントのオペレーターです。  
  
 [dbo.sysproxies](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
 に関する情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント プロキシ アカウント。  
  
 [dbo.sysproxylogin](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)  
 記録[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインは、それぞれに関連付けられた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント プロキシ アカウント。  
  
 [dbo.sysproxysubsystem](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)  
 記録[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各プロキシ アカウントでエージェント サブシステムを使用します。  
  
 [dbo.sysschedules](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ スケジュールに関する情報を格納します。  
  
 [dbo.syssessions](../../relational-databases/system-tables/dbo-syssessions-transact-sql.md)  
 含まれています、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの開始日の各[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント セッション。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービスが開始されるたびに、セッションが作成されます。  
  
 [dbo.syssubsystems](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)  
 使用可能なすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのプロキシ サブシステムに関する情報を格納します。  
  
 [dbo.systargetservergroupmembers](../../relational-databases/system-tables/dbo-systargetservergroupmembers-transact-sql.md)  
 マルチサーバー グループに現在参加している対象サーバーを記録します。  
  
 [dbo.systargetservergroups](../../relational-databases/system-tables/dbo-systargetservergroups-transact-sql.md)  
 マルチサーバー環境に現在参加している対象サーバー グループを記録します。  
  
 [dbo.systargetservers](../../relational-databases/system-tables/dbo-systargetservers-transact-sql.md)  
 マルチサーバー操作ドメインに現在参加している対象サーバーを記録します。  
  
 [dbo.systaskids](../../relational-databases/system-tables/dbo-systaskids-transact-sql.md)  
 以前のバージョンで作成されたタスクのマッピングを格納[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]現在のバージョンでのジョブ。  
  
  
