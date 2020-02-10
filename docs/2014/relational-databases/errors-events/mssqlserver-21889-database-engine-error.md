---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 262b2c795da92b2ef32c6956d9a2deda0e45a39d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62915229"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21889|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21889|  
|メッセージ テキスト|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス '%s' はレプリケーション パブリッシャーではありません。 このインスタンスがパブリッシング データベース '%s' をホストできるようにするには、`sp_adddistributor` インスタンス '%s' で、ディストリビューター '%s' を指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行します。 元のパブリッシャーで使用されているものと同じログインおよびパスワードを指定していることを確認してください。|  
  
## <a name="explanation"></a>説明  
 パブリッシャー データベースをホストするためには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがレプリケーション パブリッシャーである必要があります。 
  `sp_validate_redirected_publisher` は、リモート サーバーで `sp_helpdistributor` を呼び出し、サーバーがレプリケーション パブリッシャーであるかどうかを判断します。 このエラーは、ストアド プロシージャ `sp_helpdistributor` を実行して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の対象のインスタンがレプリケーション パブリッシャーでないことが示された場合に発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 パブリッシャー データベースをホストする `sp_adddistributor` のインスタンスで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行します。 
  `sp_adddistributor` を実行するときに、正しいディストリビューターを指定します。 がディストリビューターで最初に実行*@password*されたとき`sp_adddistributor`に使用したのと同じ値をパラメーターとして使用します。  
  
  
