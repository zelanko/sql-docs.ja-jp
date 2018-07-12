---
title: MSSQLSERVER_18752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c61d4634fa4f82ffc70748ff185ff8294f50063f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421901"
---
# <a name="mssqlserver18752"></a>MSSQLSERVER_18752
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|18752|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|REPL_INUSE|  
|メッセージ テキスト|同時にデータベースに接続できるログ リーダー エージェントまたはログ関連のプロシージャ (sp_repldone、sp_replcmds、および sp_replshowcmds) は 1 つだけです。 ログ関連のプロシージャを実行した場合、そのプロシージャが実行された接続を削除するか、その接続に対して sp_replflush を実行してから、ログ リーダー エージェントを開始するか、別のログ関連のプロシージャを実行してください。|  
  
## <a name="explanation"></a>説明  
 同時にデータベースに接続できるログ リーダー エージェントまたはログ関連のプロシージャは 1 つだけです。  
  
## <a name="user-action"></a>ユーザーの操作  
 同じパブリッシング データベースに対して他のログ リーダーが実行されていないこと、および sp_replcmds/sp_repltrans/sp_repldone を実行した後に、running sp_replflush を実行していない、または切断していないアクティブな接続が他にないことを確認します。  
  
  
