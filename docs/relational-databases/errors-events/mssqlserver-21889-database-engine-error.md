---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 177da1486d7cab622bacaea56cd886bd8dc06d06
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "72251490"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21889|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21889|  
|メッセージ テキスト|SQL サーバー インスタンス '%s' はレプリケーション パブリッシャーではありません。 このインスタンスがパブリッシング データベース '%s' をホストできるようにするために、SQL Server インスタンス '%s' で、ディストリビューター '%s' を指定して **sp_adddistributor** を実行します。 元のパブリッシャーで使用されているものと同じログインおよびパスワードを指定していることを確認してください。|  
  
## <a name="explanation"></a>説明  
パブリッシャー データベースをホストするためには、SQL Server のインスタンスがレプリケーション パブリッシャーである必要があります。 **sp_validate_redirected_publisher** は、リモート サーバーで **sp_helpdistributor** を呼び出し、サーバーがレプリケーション パブリッシャーであるかどうかを判断します。 このエラーは、SQL Server のターゲット インスタンスがレプリケーション パブリッシャーではないことを示します。  
  
## <a name="user-action"></a>ユーザーの操作  
パブリッシャー データベースをホストする SQL Server のインスタンスで **sp_adddistributor** を実行します。 **sp_adddistributor** を実行するときに、正しいディストリビューターを指定します。 *\@password* パラメーターには、ディストリビューターで **sp_adddistributor** を最初に実行したときに使用したものと同じ値を使用します。  
  
