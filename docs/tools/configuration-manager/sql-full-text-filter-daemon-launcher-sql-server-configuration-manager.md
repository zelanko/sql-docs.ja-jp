---
title: "SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
caps.latest.revision: "8"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 324fc9e1d780d885aa90b2147ef563742dedcb43
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]以降で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]で SQL フルテキスト フィルター デーモン ランチャー (FDHOST ランチャー) サービスが使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト検索をフルテキスト検索フィルター処理や単語区切りフィルター デーモン ホスト プロセスを開始します。 フルテキスト検索を使用するには、このサービスが実行されている必要があります。 FDHOST ランチャー サービスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のインスタンスに関連付けられているインスタンス対応のサービスです。 FDHOST ランチャー サービスにより、開始された各フィルター デーモン ホスト プロセスにサービス アカウント情報が反映されます。 フィルター デーモン ホスト プロセスの詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「フルテキスト検索のアーキテクチャ」を参照してください。  
  
  
