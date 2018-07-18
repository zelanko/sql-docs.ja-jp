---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8472fe5f18515adae38725234a43c130d3108d0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415911"
---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
    
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
  
  
