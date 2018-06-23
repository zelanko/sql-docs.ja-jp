---
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03342dbc069203a6ae8e06040dcf399a5f8911be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177772"
---
# <a name="mssqlserver15404"></a>MSSQLSERVER_15404
    
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
  
  