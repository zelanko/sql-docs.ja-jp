---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
caps.latest.revision: "6"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 0c2b430c438dffd8a38008be9ce9d43ab54d1a15
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21889|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21889|  
|メッセージ テキスト|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス '%s' はレプリケーション パブリッシャーではありません。 このインスタンスがパブリッシング データベース '%s' をホストできるようにするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス '%s' で、ディストリビューター '%s' を指定して **sp_adddistributor** を実行します。 元のパブリッシャーで使用されているものと同じログインおよびパスワードを指定していることを確認してください。|  
  
## <a name="explanation"></a>説明  
パブリッシャー データベースをホストするためには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがレプリケーション パブリッシャーである必要があります。 **sp_validate_redirected_publisher** は、リモート サーバーで **sp_helpdistributor** を呼び出し、サーバーがレプリケーション パブリッシャーであるかどうかを判断します。 このエラーは、ストアド プロシージャ **sp_helpdistributor** を実行して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の対象のインスタンがレプリケーション パブリッシャーでないことが示された場合に発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
パブリッシャー データベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで **sp_adddistributor** を実行します。 **sp_adddistributor** を実行するときに、正しいディストリビューターを指定します。 *@password* パラメーターには、ディストリビューターで **sp_adddistributor** を最初に実行したときに使用したものと同じ値を使用します。  
  
