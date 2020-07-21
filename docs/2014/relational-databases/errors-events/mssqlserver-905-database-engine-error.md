---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2db51e80ebe7df5f8793dba3b2c09e2afc199b59
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553117"
---
# <a name="mssqlserver_905"></a>MSSQLSERVER_905
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|905|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBSTARTUP_EE_PARTITIONING|  
|メッセージ テキスト|データベース '%.*ls' は、このエディションの SQL Server では起動できません。このデータベースには、パーティション関数 '%.\*ls' が含まれています。 パーティション分割は SQL Server Enterprise Edition でしかサポートされません。|  
  
## <a name="explanation"></a>説明  
 データベースに 1 つ以上のパーティション テーブルまたはパーティション インデックスが含まれています。 このエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではパーティション分割を使用できません。 したがって、データベースを正常に起動できません。 パーティション テーブルとパーティション インデックスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 sp_detach_db ストアド プロシージャを使用してデータベースをデタッチします。 必要であればファイルを移動してから、CREATE DATABASE で FOR ATTACH オプションまたは FOR ATTACH_REBUILD_LOG オプションを使用し、サポートされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エディションのインスタンスにデータベースをアタッチします。 すべてのテーブルのパーティションを無効にし、パーティション関数を削除します。 もう一度、データベースをデタッチしてから、現在のサーバーにデータベースを再アタッチします。  
  
  
