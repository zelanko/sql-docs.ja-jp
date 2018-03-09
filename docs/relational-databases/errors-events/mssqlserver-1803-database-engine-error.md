---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 013012ceb495ceb0b5b9e8fc207c9775713a8d5f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1803|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NO_SPACE|  
|メッセージ テキスト|CREATE DATABASE が失敗しました。 プライマリ ファイルは、model データベースのコピーを格納するために少なくとも %d MB にしてください。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、model データベースのコピーを作成することによって、データベースを作成します。 その後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってコピーの名前が変更され、新しいデータベースが要求されたサイズに拡張されます。 この場合は、ユーザーが model データベースよりも小さいデータベースの作成を試みました。 この操作は、model データベースのコピーがプライマリ データ ファイルに収まらなかったため失敗しました。これは、プライマリ データ ファイルが model データベースより小さいことが原因です。  
  
## <a name="user-action"></a>ユーザーの操作  
データベース ファイルのサイズを大きくして、データベースを作成します。 その後で、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または DBCC SHRINKDATABASE ステートメントを使用して、必要に応じてデータベースを圧縮します。  
  
