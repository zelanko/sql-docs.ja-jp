---
title: MSSQLSERVER_15404 | Microsoft Docs
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
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53c6038dbe35abbf0a5304e8f3f62374cfd9281f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver15404"></a>MSSQLSERVER_15404
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|15404|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_NTGRP_ERROR|  
|メッセージ テキスト|Windows NT グループまたはユーザー '*user*' に関する情報を取得できませんでした。エラー コード *code*。|  
  
## <a name="explanation"></a>説明  
無効なプリンシパルが指定された場合は、15404 が認証に使用されます。 そうしないと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントと Windows アカウントのドメインとの完全信頼リレーションシップがないために、アカウントの権限借用が失敗します。  
  
## <a name="user-action"></a>ユーザーの操作  
Windows プリンシパルが存在し、スペルが誤っていないことを確認します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントと Windows アカウントのドメインとの完全信頼リレーションシップがないことが、このエラーの原因である場合、次のいずれかの操作でエラーを解決できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの Windows ユーザーと同じドメインからのアカウントを使用します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が Network Service や Local System などのコンピューター アカウントを使用している場合は、Windows ユーザーを含むコンピューターはドメインから信頼されます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用します。  
  
