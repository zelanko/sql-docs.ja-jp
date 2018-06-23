---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d84961f4903ac6dd0a950ceaa8a8fb9368efcf6d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085892"
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|905|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBSTARTUP_EE_PARTITIONING|  
|メッセージ テキスト|データベース '%.*ls' は、このエディションの SQL Server では起動できません。このデータベースには、パーティション関数 '%.\*ls' が含まれています。 パーティション分割は SQL Server Enterprise Edition でしかサポートされません。|  
  
## <a name="explanation"></a>説明  
 データベースに 1 つ以上のパーティション テーブルまたはパーティション インデックスが含まれています。 このエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではパーティション分割を使用できません。 したがって、データベースを正常に起動できません。 パーティション テーブルとパーティション インデックスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 各エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[SQL Server 2014 のエディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。  
  
## <a name="user-action"></a>ユーザーの操作  
 sp_detach_db ストアド プロシージャを使用してデータベースをデタッチします。 必要であればファイルを移動してから、CREATE DATABASE で FOR ATTACH オプションまたは FOR ATTACH_REBUILD_LOG オプションを使用し、サポートされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エディションのインスタンスにデータベースをアタッチします。 すべてのテーブルのパーティションを無効にし、パーティション関数を削除します。 もう一度、データベースをデタッチしてから、現在のサーバーにデータベースを再アタッチします。  
  
  