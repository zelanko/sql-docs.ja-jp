---
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1bf1e56219b7d26e326b69d9a2f2d88afdd8c4a9
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553777"
---
# <a name="mssqlserver_15404"></a>MSSQLSERVER_15404
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
  
  
