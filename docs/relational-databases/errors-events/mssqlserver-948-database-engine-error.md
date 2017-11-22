---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: "948"
helpviewer_keywords: 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 623d41edf08c22abc958321ec77ea7e1bf0b5421
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver948"></a>MSSQLSERVER_948
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|948|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NA|  
|メッセージ テキスト|データベース '%.*ls' のバージョンは %d なので、開けません。 このサーバーではバージョン %d 以前がサポートされます。 このダウングレード パスはサポートされません。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部の機能は、データベース ファイルの構造に影響を与えます。 データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにアタッチする場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のバージョンが違っていると、ファイル形式の互換性がない場合があります。  
  
たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack 2 以降のバージョンで vardecimal ストレージ形式を使用して、それよりも前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] でデータベース ファイルをアタッチしようとすると、このエラーが発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
元のサーバーで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを判断します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、サーバーを右クリックして **[プロパティ]** をクリックするか、クエリ ウィンドウで「**SELECT @@VERSION**」と入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の元のバージョンを使用してデータベースを開きます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、元のデータベースで有効になっている機能を調べます。 データベースをアタッチする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンで使用できるように、これらの設定を修正します。  
  
