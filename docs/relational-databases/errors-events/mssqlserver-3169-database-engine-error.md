---
title: MSSQLSERVER_3169 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: "3169"
helpviewer_keywords: 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 0ceb8613d406c47c140165d0d67d2326e912a9d9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver3169"></a>MSSQLSERVER_3169
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3169|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NA|  
|メッセージ テキスト|データベースはバージョン %ls を実行中のサーバーにバックアップされました。 このバージョンは、このサーバー (バージョン %ls を実行) とは互換性がありません。 バックアップをサポートしているサーバーでデータベースを復元するか、またはこのサーバーと互換性のあるバックアップを使用してください。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部の機能は、データベース ファイルの構造に影響を与えます。 データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスに復元する場合、ファイル形式が [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の別のバージョンと互換性がない可能性があります。  
  
たとえば、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 以降のバージョンで vardecimal ストレージ形式を使用して、それよりも前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でデータベース ファイルを復元しようとすると、このエラーが発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
元のサーバーで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを判断します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、サーバーを右クリックして **[プロパティ]** をクリックするか、クエリ ウィンドウで「**SELECT @@VERSION**」と入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の元のバージョンを使用してデータベースを開きます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、元のデータベースで有効になっている機能を調べます。 データベースの復元先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンで使用できるように、これらの設定を修正します。  
  
